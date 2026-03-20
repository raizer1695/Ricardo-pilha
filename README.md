# Ricardo-pilha

Estática 

    public class PilhaEstatica {
    private int topo;
    private int[] dados;
    private int capacidade;

    public PilhaEstatica(int capacidade) {
        this.capacidade = capacidade;
        this.dados = new int[capacidade];
        this.topo = -1; // Pilha começa vazia
    }

    public boolean estaVazia() {
        return topo == -1;
    }

    public boolean estaCheia() {
        return topo == capacidade - 1;
    }

    public void empilhar(int valor) {
        if (estaCheia()) {
            System.out.println("Erro: Pilha cheia!");
            return;
        }
        dados[++topo] = valor;
    }

    public int desempilhar() {
        if (estaVazia()) {
            System.out.println("Erro: Pilha vazia!");
            return -1;
        }
        return dados[topo--];
    }

    public int topo() {
        if (estaVazia()) {
            System.out.println("Pilha vazia!");
            return -1;
        }
        return dados[topo];
    }

    public void mostrar() {
        for (int i = topo; i >= 0; i--) {
            System.out.println(dados[i]);
        }
    }
        public int tamanho() {
            return topo + 1;
        }

        public void limpar() {
            topo = -1;
        }

        public boolean contem(int valor) {
            for (int i = 0; i <= topo; i++) {
                if (dados[i] == valor) {
                    return true;
                }
            }
            return false;
    }}

Dinâmica

    class No {
    int valor;
    No proximo;

    public No(int valor) {
        this.valor = valor;
        this.proximo = null;
    }}
    
    
    class PilhaDinamica {
    private No topo;

    public boolean estaVazia() {
        return topo == null;
    }

    public void empilhar(int valor) {
        No novo = new No(valor);
        novo.proximo = topo;
        topo = novo;
    }

    public int desempilhar() {
        if (estaVazia()) {
            System.out.println("Erro: Pilha vazia!");
            return -1;
        }
        int valor = topo.valor;
        topo = topo.proximo;
        return valor;
    }

    public int topo() {
        if (estaVazia()) {
            System.out.println("Pilha vazia!");
            return -1;
        }
        return topo.valor;
    }

    public void mostrar() {
        No atual = topo;
        while (atual != null) {
            System.out.println(atual.valor);
            atual = atual.proximo;
        }
    }
        public int tamanho() {
            int contador = 0;
            No atual = topo;

            while (atual != null) {
                contador++;
                atual = atual.proximo;
            }

            return contador;
        }

        public void limpar() {
            topo = null;
        }

        public boolean contem(int valor) {
            No atual = topo;

            while (atual != null) {
                if (atual.valor == valor) {
                    return true;
                }
                atual = atual.proximo;
            }

            return false;
    }}

  Main
    
    public class Main {
    public static void main(String[] args) {

        System.out.println("=== PILHA ESTÁTICA ===");
        PilhaEstatica pilha = new PilhaEstatica(5);

        pilha.empilhar(10);
        pilha.empilhar(20);
        pilha.empilhar(30);

        pilha.mostrar();

        System.out.println("Removido: " + pilha.desempilhar());
        System.out.println("Topo: " + pilha.topo());

        System.out.println("Tamanho: " + pilha.tamanho());
        System.out.println("Contém 20? " + pilha.contem(20));

        pilha.limpar();
        System.out.println("Após limpar, está vazia? " + pilha.estaVazia());


        System.out.println("\n=== PILHA DINÂMICA ===");
        PilhaDinamica pilhaDinamica = new PilhaDinamica();

        pilhaDinamica.empilhar(100);
        pilhaDinamica.empilhar(200);
        pilhaDinamica.empilhar(300);

        pilhaDinamica.mostrar();

        System.out.println("Removido: " + pilhaDinamica.desempilhar());
        System.out.println("Topo: " + pilhaDinamica.topo());

        System.out.println("Tamanho: " + pilhaDinamica.tamanho());
        System.out.println("Contém 200? " + pilhaDinamica.contem(200));

        pilhaDinamica.limpar();
        System.out.println("Após limpar, está vazia? " + pilhaDinamica.estaVazia());
    }}

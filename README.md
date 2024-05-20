# atividade-empregado
import com.mycompany.exercicio.Empregado;
import java.util.*;

package com.mycompany.exercicio;

/**
 *
 * @author 324117924
 */
public class Exercicio {

    public static void main(String[] args) {
        Scanner leitor = new Scanner(System.in);
        ArrayList<Empregado> empregados = new ArrayList<Empregado>(); 
            
        System.out.println("Selecione uma opção: ");
        System.out.println("1 - Criar novo empregado");
        System.out.println("2 - Promover empregado");
        System.out.println("3 - Aumentar salário empregado");
        System.out.println("4 - Demitir empregado");
        System.out.println("5 - Fazer aniversário do empregado");
        System.out.println("6 - Sair");
        int opcao = leitor.nextInt();
        
        switch (opcao) {
            case 1:
                Empregado emp = new Empregado();
                
                System.out.println("Digite o nome do empregado: ");
                String nome = leitor.next();
                emp.setNome(nome);
                
                System.out.println("Digite a idade do empregado: ");
                int idade = leitor.nextInt();
                emp.setIdade(idade);
                
                System.out.println("Digite o salário do empregado: ");
                double salario = leitor.nextDouble();
                emp.setSalario(salario);
                
                empregados.add(emp);
                System.out.println("Empregado " + emp.getNome() + " criado!");
            case 2:
                System.out.println("Digite o número do empregado: ");
                for (int i = 0; i < empregados.size(); i++) {
                    System.out.println(i + " - " + empregados.get(i));
                }
                int indice = leitor.nextInt();
                
                Empregado empregado = empregados.get(indice);
                empregado.promover();
        }
    }
}/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package com.mycompany.exercicio;

/**
 *
 * @author 324117924
 */
public class Empregado {
    private String nome;
    private int idade;
    private double salario;
    
    public String getNome() {
        return this.nome;
    }
    
    public int getIdade() {
        return this.idade;
    }
    
    public double getSalario() {
        return this.salario;
    }
    
    public void setNome(String nome) {
        this.nome = nome;
    }
    
    public void setIdade(int idade) {
        this.idade = idade;
    }
    
    public void setSalario(double salario) {
        this.salario = salario;
    }
    
    public void promover() {
        if (this.idade > 18) {
            aumentarSalario(25);
            System.out.println("O empregado " + this.nome + " foi promovido!");
        } else {
            System.out.println("O empregado não tem idade necessária");
        }
    }
    
    public void aumentarSalario(double percent) {
        this.salario = (percent * this.salario / 100) + this.salario;
    }
    
    // 1 justa causa, 2 decisão empregador, 3 aposentadoria
    public void demitir(int motivo) {
        switch (motivo) {
            case 2:
                double multa = 40 * this.salario / 100;
                System.out.println("O empregado deverá pagar " + multa + " de multa");
                break;
            case 3:
                if (this.salario > 1000 && this.salario < 2000) {
                    this.salario = 1500;
                } else if (this.salario > 2001 && this.salario < 3000) {
                    this.salario = 2500;
                } else if (this.salario > 3001 && this.salario < 4000) {
                    this.salario = 3500;
                } else {
                    this.salario = 4000;
                }   break;
            default:
                System.out.println("O empregado deverá cumprir aviso prévio");
                break;
        }
    }
    
    public void fazerAniversario() {
        this.idade++;
    }
}

# Proyecto-1

import java.util.Scanner;

    public class Principal{
       public static void main (String []args){
       Principal.mostrarMenu();
      } 
      
        public static void mostrarMenu(){  
       int s = 1;
            while(s != 0){
        //Vehiculo
          System.out.println("Ingrese un numero");   
          System.out.println("Si ingresa 0, ACABA EL PROGRAMA.");   
          System.out.println("Si ingresa 1, CREAR VEHICULO.");  
          System.out.println("Si ingresa 2 muestra por pantalla la información de todos los vehículos almacenados hasta el momento");
          System.out.println("Si ingresas 3, muestra por pantalla la información de la cantidad de vehículos creados hasta el momento ");
        System.out.println("Si ingresa 4, muestra por pantalla la información de todos los vehículos que tengan color “verde” ");
          System.out.println("Si ingresa 5, muestra por pantalla la información de todos los vehículos que tengan modelo entre 2000 y 2021  ");
        //sensor
          System.out.println("Si ingresa 6, CREAR SENSOR");
          System.out.println("Si ingresa 7, muestra por pantalla la información de todos los sensores almacenados hasta el momento.");
          System.out.println("Si ingresa 8, muestra por pantala la informacion de la cantidad de sensores creados hasta el momento .");
          System.out.println("Si ingresa 9, muestra por pantalla la información de todos los sensores qeu son de tipo temperatura.");
          System.out.println("Si ingresa 666, muestre por pantalla los sensores tipo temperatura ordenados por valor");

          Scanner entrada = new Scanner(System.in);


          int persona = entrada.nextInt();
          if (persona ==  0){
           System.out.println("Acaba el programa");
           break;
          }
          if (persona ==  1){ 
          if (Vehiculo.posAnadir>= Vehiculo.listaVehiculos.length){
          System.out.println("Base de datos llena");
          } else{
          int modelo = entrada.nextInt();
          String marca = entrada.next();
          double valorComercial = entrada.nextDouble();
          String color = entrada.next();
          Vehiculo v= new Vehiculo(modelo, marca,valorComercial,color);
          }
        }
    
        if(persona ==2){
        System.out.println("La infoemación de los vehiculos es: \n" + Vehiculo.toStringVehiculos());
        }
        if(persona ==3){
        System.out.println(Vehiculo.cantidadVehiculos()); 
        }
        if(persona ==4){
        System.out.println(Vehiculo.verdes());
        }
        if(persona ==5){
        System.out.println(Vehiculo.actual());
        }
        
        if (persona ==  6){
        if (Sensor.posAnadir>= Sensor.listaSensor.length){
          System.out.println("Base de datos llena");
        } else{
        String tipo = entrada.next();
        double valor = entrada.nextDouble();
        Sensor ss= new Sensor(tipo,valor);

        }
       }
       
       if (persona == 7){
        System.out.println("Todos los sensores almacenados hasta el momento son: \n" + Sensor.toStringSensores());   
       }
       
       if (persona == 8){
        System.out.println(Sensor.cantidadSensores());   
       }
       
       if (persona == 9){
        System.out.println(Sensor.temp());
       }
       if (persona ==  666){
        Sensor tem = new Sensor();
        System.out.println(tem.temperaturas());
       }
      }
   }
}
--------------------------------------------------------------------------------------------------------------------------
 public class Vehiculo{
    public static int tamano = 10;
    public static Vehiculo listaVehiculos[] = new Vehiculo [tamano];
    public static int posAnadir = 0;
   
    private int modelo;
    private String marca;
    private double valorComercial;
    private String color;
   
       
    public Vehiculo (int mo, String ma,double va){
       this.modelo = mo;
       this.marca = ma;
       this.valorComercial = va;  
       this.color = "verde";
    }
   
    public Vehiculo (int mo, String ma, double va, String co){
       this.modelo = mo;
       this.marca = ma;
       this.valorComercial = va;
       this.color = co;
       Vehiculo.listaVehiculos [posAnadir] = new Vehiculo (modelo,marca,valorComercial,color);
       posAnadir++;
       

    }
   
    public int getMo(){
        return this.modelo;
    }
   
    public String getMa(){
        return this.marca;
    }
   
    public double getVa(){
        return this.valorComercial;
    }
   
    public String getCo(){
        return this.color;
    }
   
    public void setMo(int mo){
        this.modelo = mo;
    }
   
    public void setMa(String ma){
        this.marca = ma;
    }
   
    public void setVa(double va){
       this.valorComercial = va;
    }
   
    public void setCo(String co){
        this.color = co;
    }

    public String toString(){
        String a = "el modelo es: "+ this.modelo + "\nla marca es: " + this.marca + "\n el valor comercial es: "+ this.valorComercial + "\n el valor del color: "+ this.color;
        return a;
    }
   
    public static String toStringVehiculos(){
        String vehiculos = "";
        for(int i = 0; i<posAnadir; i++){
            vehiculos = vehiculos + listaVehiculos[i].toString();
       
        }
        return vehiculos;
    }
   
   
   
   
    public static int cantidadVehiculos () {
        int a = posAnadir;
       
       
        return a;
    }
    public static Vehiculo [] verdes(){
       Vehiculo [] listaverdes = new Vehiculo [posAnadir];
       int e = 0;
     for(int i = 0; i<=posAnadir; i++){
         if (listaVehiculos[i].getCo().equals("verde")){
           listaverdes[e]= listaVehiculos[i];
           e++;
        }
        }
        return listaverdes;
     }
    
    public static Vehiculo [] actual(){
       Vehiculo [] listaActual = new Vehiculo [posAnadir];
       int e = 0;
     for(int i = 0; i<=posAnadir; i++){
         if (listaVehiculos[i].getMo()>=2000 && listaVehiculos[i].getMo()>=2021){
           listaActual[e]= listaVehiculos[i];
           e++;
        }
        }
        return listaActual;
     }
}
--------------------------------------------------------------------------------------------------------

import java.util.Arrays;
public class Sensor {
 public static Sensor listaSensor[] = new Sensor [8];
 public static int tamano = 8;
 public static int posAnadir = 0;

 
 private String tipo;
 private double valor;
 
 
 public Sensor(){}
 
 public Sensor(String t, double v){
    this.tipo = t;
    this.valor = v;
    listaSensor[posAnadir] = new Sensor(t,v);
    posAnadir++;
    }
   
 public  String getTi(){
     return this.tipo;
 }
 
 public double getVa(){
     return this.valor;
 }
 
 public void setTi(String t){
     this.tipo = t;
 }
 
 public void setVa(double v){
     this.valor = v;
 }
 
 public static Sensor [] temperaturas(){
     Sensor [] listatemperatura = new Sensor [posAnadir];
    int contador = 0;
    int e = 0;

    for(int i = 0; i<=posAnadir; i++){
         if (listaSensor[i].getTi().equals("temperatura")){
        contador = contador + 1 ;
        listatemperatura[e]= listaSensor[i];
        e++;
        }
        }
    Arrays.sort(listatemperatura);
   
    return listatemperatura;
     
    }
 
 public String toString(){
        String a = "el tipo es : "+ this.tipo + "\n El valor es: " + this.valor;         
        return a;
    }
   
    public static String toStringSensores(){
        String sensores = "";
        for(int i = 0; i<posAnadir; i++){
            sensores = sensores + listaSensor[i].toString();
       
        }
        return sensores;
    }
   
   
   
   
    public static int cantidadSensores () {
        int a = posAnadir;
       
       
        return a;
    }
    
    public static Sensor [] temp(){
       Sensor [] listatemp = new Sensor [posAnadir];
       int e = 0;
     for(int i = 0; i<=posAnadir; i++){
         if (listaSensor[i].getTi().equals("temperatura")){
           listatemp[e]= listaSensor[i];
           e++;
        }
        }
        return listatemp;
     }
    
    
}

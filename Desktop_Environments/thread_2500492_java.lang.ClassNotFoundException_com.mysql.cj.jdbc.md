---
title: "java.lang.ClassNotFoundException: com.mysql.cj.jdbc.Driver even if classpath setted"
date: 2024-09-03
forum: Desktop Environments
---

### Post by arielcrespin on 2024-09-03
Hi everybody.
My problem is this: java.lang.ClassNotFoundException: com.mysql.cj.jdbc.Driver, from linux terminal, even with CLASSPATH="/var/www/html/java/mysql.jar".
The full error message from terminal is:
> 
        java.lang.ClassNotFoundException: com.mysql.cj.jdbc.Driver
    at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:581)
    at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:178)
    at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:527)
    at java.base/java.lang.Class.forName0(Native Method)
    at java.base/java.lang.Class.forName(Class.java:315)
    at mysql.main(mysql.java:13)
java.lang.NullPointerException
    at mysql.main(mysql.java:39)
This is my source code from mysql.java :
```
import java.sql.Connection;
import java.sql.Statement;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.ResultSetMetaData;
import java.sql.SQLException;
public class mysql {
    public static void main(String args[]) {
        Connection conexion=null;
        Statement instruccion=null;
        ResultSet conjuntoresultados=null;
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            conexion=DriverManager.getConnection("jdbc:mysql://localhost:3306/galpon","root","password");
            instruccion=conexion.createStatement();
            conjuntoresultados=instruccion.executeQuery("select usuario,cbu from duenos");
            ResultSetMetaData metadatos=conjuntoresultados.getMetaData();
            int numerocolumnas=metadatos.getColumnCount();
            System.out.printf("Dueños de vehículos:");
            for(int i=0;i<numerocolumnas;i++)
                System.out.printf("%-8s\t",metadatos.getColumnName(i));
            System.out.println();
            while(conjuntoresultados.next()){
                for(int i=0;i<numerocolumnas;i++)
                    System.out.printf("%-8s\t",conjuntoresultados.getObject(i));
                System.out.println();
            }
        }
        catch (SQLException sqlexcepcion) {
            sqlexcepcion.printStackTrace();
        }
        catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
        finally
        {
            try
            {
                conjuntoresultados.close();
                instruccion.close();
                conexion.close();
            }
            catch ( Exception excepcion )
            {
                excepcion.printStackTrace();
            }
        }
    }
}
```
I have ubuntu 20.04.6, openjdk 11, mysql connector 8.0.20 (the only provided from mysql downloads for ubuntu 20).
CLASPATH is set in ~/.bashrc.
What am i doing wrong?

---


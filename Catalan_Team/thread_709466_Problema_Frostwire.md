---
title: "Problema Frostwire"
date: 2008-02-27
forum: Catalan Team
---

### Post by eduardsola on 2008-02-27
Bé, com vaig explicar en un altre post, no puc iniciar el Frostwire, vaig instal·lar els paquets que hi ha al Synaptic del sun-java6 i continua sense arrencar.

El problema està a quan li dono al botó per arrencar, que no fa res, ni s'immuta.

Si l'executo pel terminal em diu lo següent:

```
geduard@geduard:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com

```

Salut!

---

### Post by papapep on 2008-02-27
Mira a veure quines opcions tens en executar:

```
sudo update-alternatives --config java
```

---

### Post by eduardsola on 2008-02-27
```
geduard@geduard:~$ sudo update-alternatives --config java

Hi ha 3 alternatives que proveeixin «java».

  Selecció     Alternativa
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-gcj/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java

Premeu retorn per a mantenir l'opció per defecte[*], o introduïu un número de selecció: 

```

I doncs? :)

---

### Post by papapep on 2008-02-27
Doncs que premis el 3 per que faci servir la mv de Sun per defecte i t'hauria de funcionar el Frostwire (i si no ho fa, ara ja no serà pel Java)

---

### Post by eduardsola on 2008-02-27
OOOOH!

Ja funciona.

Gràcies papapep, no sé què faria sense tu.:)


Apa, salut!

---


---
title: "Ayuda con JAVA 6 en UBUNTU 10.04"
date: 2012-04-09
forum: Colombia Team - Colombia
---

### Post by carlosgonzalca on 2012-04-09
Buenos dias, muchachos de UBUNTU-CO, recurro a ustedes después de naufragar por la red.

Sucede que los señores de ORACLE han quitado el acuerdo de licencia y por ende en los repositorios oficiales de ubuntu PARTNER, ya no esta disponible el JRE ni JDK de JAVA 6 ni 7, así es que solicito su colaboración para poder instalar la maquina virtual o JRE para poder desplegar servicios de MI OPENFIRE, el cual requiere JAVA para su funcionamiento.

He mirado que en la pagina oficial de java esta el codigo fuente y un paquete RPM, el cual se puede convertir con la herramienta alien a .DEB, pero creo que no es buena práctica, o espero primero sus opiniones a ver que puedo hacer.

---

### Post by yogova9 on 2012-04-10
amigo acá te dejo este link que encontré referente a tu pregunta.

[http://www.ubuntu-guia.com/2011/10/instalar-oracle-java-ubuntu-1110.html#more](http://www.ubuntu-guia.com/2011/10/instalar-oracle-java-ubuntu-1110.html#more)

espero te sirva. cuentas como te fue.

---

### Post by AnelayTynclic on 2012-06-12
gracias a Dios por intiresny

---

### Post by darkhole on 2012-06-12
Ten en cuenta, la recomendacion que te dieron es para instalar OpenJDK, que si bien es casi casi como el Java de Oracle, no lo es en un 100%. Algunas aplicaciones tienen complicaciones con OpenJDK, por lo que requieren el Java de Oracle, para instalarlo de la manera mas adecuada, puedes usar el siguiente script:

[http://blog.flexion.org/2012/01/16/install-sun-java-6-jre-jdk-from-deb-packages/](http://blog.flexion.org/2012/01/16/install-sun-java-6-jre-jdk-from-deb-packages/)

Con este se crea un repositorio local y se compilan los paquetes .deb, por lo cual es el metodo mas limpio para instalar el Oracle de Java (version 6 o la 7)

---


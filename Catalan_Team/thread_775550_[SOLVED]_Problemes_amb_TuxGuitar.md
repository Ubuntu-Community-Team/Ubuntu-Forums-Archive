---
title: "[SOLVED] Problemes amb TuxGuitar"
date: 2008-04-30
forum: Catalan Team
---

### Post by LitusMayol on 2008-04-30
Bones!

He installat una Ubuntu i l'he convertit en UbuntuStudio. He instal·lat el TuxGuitar amb l'instal·lador gràfic (Afegeix/Elimina...). M'apareix al al menú com seria d'esperar,però quan l'engego no passa re. Simplement re. I si faig "gksu tuxguitar" passa això:
```

litus@UbuntuStuio:~$ gksu tuxguitar
litus@UbuntuStuio:~$
```

Com podeu veure re. Tinc una Ubuntu en una altra partició i no hi tinc cap problema, no ho entenc.

Algú em pot ajudar?



Merci, i perdoneu el novell! ;)

---

### Post by menut on 2008-04-30
Instal·la estos paquets:

libitext-java

libswt3.2-gtk-java

sun-java6-jre

java2-runtime

Font:
> [http://www.ubuntu-es.org/index.php?q=node/86313](http://www.ubuntu-es.org/index.php?q=node/86313)

---

### Post by LitusMayol on 2008-04-30
> **menut said:**
> Instal·la estos paquets:

libitext-java

libswt3.2-gtk-java

sun-java6-jre

java2-runtime

Font:

Renoi nano! Ràpid i eficient.Jo havia instal·lat aquests: 
```

sun-java5-jre libswt3.2-gtk-jni libswt3.2-gtk-java

```
Suposo que ja es deuen haver quedat obsolets.
Merci de nou **menut**!

:guitar:

---

### Post by lo gambusí on 2008-05-01
si l'instal·les des del synaptic t'afegix automàticament tots estos fitxers ;)

---

### Post by CarlesOriol on 2008-05-02
gksu tuxguitar???????

Per què executes el tuxguitar com a usuari administrador?? amb un simple tuxguitar n'hi ha prou i va de conya.

---

### Post by PellRoja on 2008-05-02
que pots fer amb el programa tuxGuitar?

---

### Post by menut on 2008-05-02
Crear, editar partitures, composar... 

[http://www.tuxguitar.com.ar/](http://www.tuxguitar.com.ar/)

---

### Post by LitusMayol on 2008-05-27
Bones!

He tornat a instal·lar l'**Ubuntu**... I al probar d'instal·lar el **TuxGuitar**...
```

litus@mayolets-desktop:~$ sudo aptitude install libitext-java libswt3.2-gtk-java sun-java6-jre java2-runtime
[sudo] password for litus: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet         
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
litus@mayolets-desktop:~$ sudo apt-get install libitext-java libswt3.2-gtk-java sun-java6-jre java2-runtime
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
litus@mayolets-desktop:~$ 
```

Alguna suggerència?

Merci!

---

### Post by papapep on 2008-05-27
```
litus@mayolets-desktop:~$ sudo aptitude install libitext-java libswt3.2-gtk-java sun-java6-jre java2-runtime
[sudo] password for litus: 
E: dpkg was interrupted, you must manually run '**[COLOR="Red"]dpkg --configure -a[/COLOR]**' to correct the problem. 
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet         
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
E: dpkg was interrupted, you must manually run '**[COLOR="Red"]dpkg --configure -a[/COLOR]**' to correct the problem. 
litus@mayolets-desktop:~$ sudo apt-get install libitext-java libswt3.2-gtk-java sun-java6-jre java2-runtime
E: dpkg was interrupted, you must manually run '**[COLOR="Red"]dpkg --configure -a[/COLOR]**' to correct the problem. 
litus@mayolets-desktop:~$
```

T'ho diu tres cops :-)

---

### Post by LitusMayol on 2008-05-27
Que bona que és la lectura...! hehe


Però ara em passa això...

```

litus@mayolets-desktop:~$ sudo apt-get install libitext-java libswt3.2-gtk-java sun-java6-jre java2-runtime
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
Reading state information... Fet         
El paquet java2-runtime és un paquet virtual proveït per:
  sun-java6-jre 6-06-0ubuntu1
  sun-java5-jre 1.5.0-15-0ubuntu1
  openjdk-6-jre 6b09-0ubuntu2
  gij-4.1 4.1.2-18ubuntu1
  java-gcj-compat 1.0.77-2ubuntu2
Necessiteu seleccionar-ne un explícitament per a instal·lar-lo.
E: El paquet java2-runtime no té candidat d'instal·lació
litus@mayolets-desktop:~$ 
```

Quin he d'escollir?

---

### Post by papapep on 2008-05-28
```
update-alternatives --config java
```

i tria la que vols que sigui la màquina virtual per defecte (t'aconsello que sigui la més nova, a no ser que algun programa tingui algun requeriment especial)

---

### Post by LitusMayol on 2008-05-28
```
litus@mayolets-desktop:~$ sudo update-alternatives --config java
[sudo] password for litus: 

Hi ha 3 alternatives que proveeixin «java».

  Selecció     Alternativa
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-gcj/jre/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Premeu retorn per a mantenir l'opció per defecte[*], o introduïu un número de selecció: 3
Using '/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide 'java'.
litus@mayolets-desktop:~$ 

```
mmm....?

---

### Post by grundt on 2008-10-21
Perdoneu, és necessari tenir l'ubuntu studio per fer funcionar el tuxguitar?

Gracies

---

### Post by papapep on 2008-10-21
No.

---

### Post by grundt on 2008-10-21
Doncs a mi em passa el mateix  que l'origen d'aquest post.

Tinc el Tuxguitar instal·lat, però quan el llanço desde: Aplicacions/So i 

Video, no passa res.

Que he de fer?

---

### Post by papapep on 2008-10-22
És millor que obris un nou fil. Que s'assembli no significa que tingueu el mateix problema.
Aprofita per invocarlo des d'un terminal, a veure quin missatge et surt, i enganxa el resultat al nou fil.

---

### Post by grundt on 2008-10-22
ok

---


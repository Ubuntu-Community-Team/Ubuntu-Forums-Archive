---
title: "[SOLVED] Tuxguitar no arrenca"
date: 2008-10-22
forum: Catalan Team
---

### Post by grundt on 2008-10-22
Hola, he instal·lat el tuxguitar desde el synaptic, crec.

A la hora de llançar-lo desde el menú aplicacions/ so i video, ho faig però no passa res.

L'he invocat desde el terminal i em diu:

/usr/bin/tuxguitar: 21: /usr/local/opt/java/jre/bin/java: not found

també l'he buscat:

grundt@grundt-desktop:~$ find / -iname tuxguitar -print 2> /dev/null
/usr/share/tuxguitar
/usr/share/menu/tuxguitar
/usr/share/doc/tuxguitar
/usr/bin/tuxguitar

---

### Post by LitusMayol on 2008-10-22
UUuuuiii!

A mi m'és familiar això! eheh Primer: no. No és necessari tenir l'**UbuntuStudio**, ni molt menys.

Jo el que vaig haver de fer va ser instal·lar aquests paquets:
```
sudo apt-get install libitext-java libswt3.2-gtk-java sun-java6-jre java2-runtime
```

Després vaig tenir problemes amb la configuració del *java* i vaig haver de fer:
```
update-alternatives --config java
```
Que si no recordo malament era per triar el java que volia fer servir... Aquí no &#347;é quina opció has de triar... Jo ho vaig fer fins que vaig trobar la que funcionava! xD

I ja per últim el podia obrir, però no repoduia el so...(encara em passa a vegades). Aleshores tanco el **TuxGuitar**, obro un terminal hi poso:
```
timidity
```
i apa-li! A córrer!


A veure si et serveix!

---

### Post by grundt on 2008-10-22
Hola, no m'en surto a l'hora de triar l'alternativa de java.

Això es el que m'ha dit al triar la segona però en totes m'ha dit lo mateix.


grundt@grundt-desktop:~$ update-alternatives --config java

Hi ha 4 alternatives que proveeixin «java».

  Selecció     Alternativa
-----------------------------------------------
          1    /usr/bin/cacao
          2    /usr/bin/gij-4.2
*+        3    /usr/lib/jvm/java-gcj/jre/bin/java
          4    /usr/bin/gij-4.1

Premeu retorn per a mantenir l'opció per defecte[*], o introduïu un número de selecció: 2
Using '/usr/bin/gij-4.2' to provide 'java'.
update-alternatives: no es pot fer l'enllaç simbòlic de /etc/alternatives/java.dpkg-tmp a /usr/bin/gij-4.2: Permission denied


Merci!

---

### Post by papapep on 2008-10-22
Ja tens instal·lat el sun-java6-jre?

---

### Post by grundt on 2008-10-23
He instalat això del sun-java6 i ara funciona correctament.

Sou uns p***s cracks!

pd. m'agradaria ajudar en algo

---

### Post by CarlesOriol on 2008-10-25
> **grundt said:**
> 
pd. m'agradaria ajudar en algo

Vine a la propera festa, passa-t'ho bé i apren... segur que és un bon començament.

[https://wiki.ubuntu.com/InstallIntr%C3%A8pid](https://wiki.ubuntu.com/InstallIntr%C3%A8pid)

---


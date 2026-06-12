---
title: "[SOLVED] Programa d'ajut de la declaració de l'Iva"
date: 2008-01-27
forum: Catalan Team
---

### Post by lpargemi on 2008-01-27
Hola

He de fer la declaració anual de l'Iva (com sempre tard) i volia instal.lar-me el programa d'ajut de la pàgina d'hisenda, que té una versió per a Linux.

Un cop superada la crisi d'arrencar l'instal.lador ;-) no em funciona [es tanca immediatament, i si l'executo en un terminal s'escriu un texte a tota velocitat i es tanca desseguida. 

Suposo que cal instal.lar la màquina virtual de java, així que també la descarrego i la instal.lo. [S'instal.la al directori on faig les descàrregues i tota mena d'experiments]. Faig córrer el ControlPanel que hi ha al directori bin que ha creat, i pel què em diu semblaria que està en marxa.

Torno a provar amb el siva7100.bin, i fa el mateix. Capturant la pantalla quan el terminal està obert (després de diverses proves, com si fés tir al plat) veig que es queixa de què no troba la màquina virtual del java on l'espera... que no sé on és, o sigui que no anem enlloc.

Sabeu com hauria d'haver-ho fet?

Salut

Lluís

PD [Lamento ser poc sofert, però aquest fil ara mateix té interès purament instructiu: a la vista de què no me'n sortia, i de què només em queden tres dies, i de què no sé si tindré massa temps, he presentat els papers a hisenda amb el portàtil de la feina, que va en W$. És que la multa pel retard ja me la vaig guanyar una vegada....]

---

### Post by pespin on 2008-01-27
Pots postejar la captura de pantalla amb els errors? :)

---

### Post by lpargemi on 2008-01-27
Ho estic provant i ara no m'en surto. S'apaga tan ràpid que no hi ha manera.

Sabeu si des d'un terminal es pot engegar amb l'opció de redireccionar la sortida a un fitxer de texte? (en teoria si que es pot direccionar, però no sé què li he de dir perquè arrenqui el programa)

lluís

---

### Post by papapep on 2008-01-28
Cal que expliquis amb més detall què has fet i com. Per exemple, no expliques quina versió has instal·lat de java, ni exactament a quin directori l'has instal·lat. Adona't de que si no ho fas, nosaltres que no som davant del teu monitor no sabem gairebé res.

A veure, verifica si tens el paquet de java dels repositoris instal·lat. En un terminal fes:

```
sudo aptitude search sun | grep java
```

i enganxa aquí el que respongui.

---

### Post by orestesmas on 2008-01-28
Hola Lluís.

Encuriosit per haver après que els de l'AEAT comencen a fer versions per GNU/Linux (ni que sigui en java privatiu, de moment), he provat els passos que em dius.

El resultat ha estat que jo sí que l'he pogut fer funcionar, però he hagut d'utilitzar EXACTAMENT la màquina virtual 1.6.0_03. Amb la darrera versió que hi ha al web de sun (_04) em petava. Això si, només és en castellà, m'ho hauria d'haver suposat.

La versió _03 l'he baixada directament de l'AEAT (a la mateixa pàgina on et baixes l'instal·lador del programa de l'IVA), perquè he suposat que ells haurien comprovat el funcionament del programa amb aquella versió.

Això si, al web de l'AEAT hi ha la versió per linux de 32 bits, així que he hagut de fer mans i mànigues per executar això en la meva Debian de 64 bits. Sort que temps enrere m'havia configurat un chroot de 32 bits per coses com aquesta...

Dit de passada, és una VERGONYA que Sun, després de CINC ANYS, encara no hagi publicat una versió del plugin de java per sistemes de 64 bits. Està clar que no es pot esperar res del desenvolupament de programari privatiu.

---

### Post by lpargemi on 2008-01-28
Hola

Jo també vaig descarregar la versió 1.6.3 de la pàgina d'hisenda i el vaig instal.lar. I em va muntar uns directoris partint del punt on faig les desàrregues, que en el meu cas és

/home/lluis/Desktop/Nyaps/

Això hi munta uns directoris tal com

/home/lluis/Desktop/Nyaps/jre1.6.0_03/

Dins d'un directori dit bin dins d'aquest arbre hi ha una cosa que es diu ControlPanel, que quan l'executes obre una finestra com aquesta:

[Aqui hi hauria l'adjunt]

 on hi diu que s'ha instal.lat (o algo) la plataforma que diu n'Orestes

Ara bé si faig córrer des del terminal l'ordre que recomanen a la pàgina d'hisenda obtinc:

> lluis@lluis:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Ja ho veieu, que hi ha instal.lada la versió 4.1.2 

L'ordre que em recomana en Papapep dóna això:

> lluis@lluis:~$ sudo aptitude search sun | grep java
p   sun-java5-bin                   - Sun Java(TM) Runtime Environment (JRE) 5.0
p   sun-java5-demo                  - Sun Java(TM) Development Kit (JDK) 5.0 dem
p   sun-java5-doc                   - Sun JDK(TM) Documention -- integration ins
p   sun-java5-fonts                 - Lucida TrueType fonts (from the Sun JRE)
p   sun-java5-jdk                   - Sun Java(TM) Development Kit (JDK) 5.0
p   sun-java5-jre                   - Sun Java(TM) Runtime Environment (JRE) 5.0
p   sun-java5-plugin                - The Java(TM) Plug-in, Java SE 5.0
p   sun-java5-source                - Sun Java(TM) Development Kit (JDK) 5.0 sou
p   sun-java6-bin                   - Sun Java(TM) Runtime Environment (JRE) 6 (
p   sun-java6-demo                  - Sun Java(TM) Development Kit (JDK) 6 demos
p   sun-java6-doc                   - Sun JDK(TM) Documention -- integration ins
p   sun-java6-fonts                 - Lucida TrueType fonts (from the Sun JRE)
p   sun-java6-javadb                - Java(TM) DB, Sun Microsystems' distributio
p   sun-java6-jdk                   - Sun Java(TM) Development Kit (JDK) 6
p   sun-java6-jre                   - Sun Java(TM) Runtime Environment (JRE) 6 (
p   sun-java6-plugin                - The Java(TM) Plug-in, Java SE 6
p   sun-java6-source                - Sun Java(TM) Development Kit (JDK) 6 sourc



Ah i l'instal.lador siva7100.bin segueix sense anar.

Bona nit

Lluís

---

### Post by papapep on 2008-01-29
Doncs si instal·les el següent paquet crec que tot et rutllarà com cal:

```
sudo aptitude install sun-java6-bin
```

---

### Post by ilku on 2008-01-29
He provat aquest siva. amb diversos ordinadors i he de dir que amb una gutsy funciona correctament, ara be amb una dapper ni instal.lant el sun-java6 com es suggereix (a la gutsy si esta)

EDITO:
Resulta que després de descarregar al nou sun-java6 com es suggeria el que em de fer es:
$sudo update-alternatives --config java

i escollir el java 6 llavors ja funciona en el dapper (suposo que es extrapolable a tots aquells que no tenen el java 6

---

### Post by lpargemi on 2008-01-29
Instal.lant la versió 1.6 del java, com suggereix en Papapep, em corre el programa per instal.lar l'ajut de l'IVA

Aleshores em dóna opció a triar la màquina virtual 1.6.0_03, com deia n'Orestes, que està instal.lada al directori que us comentava (el que tinc configurat per les descàrregues).

A partir d'aquí ja funciona, això si, només en castellà.

Després se'm genera un altre problema, però quan el documenti el comento a un altre fil. Aquest el donaré per solucionat.

Gràcies per tot

Lluís

---


---
title: "Problemes per actualitzar amsn 0.97"
date: 2008-04-28
forum: Catalan Team
---

### Post by lFossil on 2008-04-28
Hola amics, ja fa dies que em surt quan obric l'amsn una finestra que em diu que hi ha una nova versió. Provo de descarregar-ho però no puc. No se com fer-ho.
Adjunto una imatge sobre la pagina que em surt
[http://img182.imageshack.us/my.php?image=capturach0.png]("http://img182.imageshack.us/my.php?image=capturach0.png")

---

### Post by patrickfromspain on 2008-04-29
quina versio d'ubuntu fas servir?? Em sembla que va sent hora d'actualizar-se no? ;)

En resposta a la pregunta: no pots segurament perque el sistema de baixar arxius a sourceforge havia canviat, si no recordo malament. Pots baixar-te l'ultima versio de l'amsn a amsn-project.net.
Si t'actualitzes a Hardy, tambe tindras l'amsn 0.97.

salut

---

### Post by menut on 2008-04-29
Usa l'Ubuntu Studio, si no m'equivoco...:-k

---

### Post by lFossil on 2008-05-01
Sí sí, estic usant l'Ubuntu Studio

---

### Post by patrickfromspain on 2008-05-01
ubuntu, ubuntustudio.. que mes dona? Al cal i a la fi, es tot el mateix no? ;)

---

### Post by CarlesOriol on 2008-05-02
En patrick es refereix a la versió gutsy, feisty... i que si us actualitzeu a Hardy això ja s'actualitzarà.

---

### Post by lFossil on 2008-05-02
Perdoneu, però jo sóc nou en l'ubuntu i això del hardy i feisty no se que són.
L'unic que sé es que tinc el gutsy gibbon 7,10 :confused:

---

### Post by patrickfromspain on 2008-05-02
7.10=Gutsy Gibbon
7.04=Feisty Fawn
8.04=Hardy Heron

Son tot versions d'ubuntu.

Primer de tot disculpa, si hagues mirat la captura una mica millor hauria vist que ja estaves fent la versio 0.97, en el teu casa la RC1.

La solucio es senzilla, en terminal:

gksudo gedit /etc/apt/sources.list

i mira que tinguis aquesta linea: deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

sense # al davant, ha d'estar tal cual te l'he posat jo. Si no la tens, afegeix-la manualment. Guardes i tanques.

sudo apt-get update
sudo apt-get dist-upgrade

hauries de tenir l'amsn entre els updates.

salut!

---

### Post by lFossil on 2008-05-02
Ei gràcies per l'aclariment, :) he fet el que mas dit, però he posat allò que mas dit al terminal després de fer el de la source list i m'ha sortit això:

jasiel@jasiel-laptop:~$ sudo apt-get update
E: El tipus «[http://archive.ubuntu.com/ubuntu/»](http://archive.ubuntu.com/ubuntu/») no és conegut en la línia 12 de la llista de fonts /etc/apt/sources.list
jasiel@jasiel-laptop:~$ sudo apt-get dist-upgrade
E: El tipus «[http://archive.ubuntu.com/ubuntu/»](http://archive.ubuntu.com/ubuntu/») no és conegut en la línia 12 de la llista de fonts /etc/apt/sources.list
E: No s'ha pogut llegir la llista de les fonts.
jasiel@jasiel-laptop:~$ 


Què hi falla?:-k

---

### Post by papapep on 2008-05-02
> Perdoneu, però jo sóc nou en l'ubuntu i això del hardy i feisty no se que són.

[https://wiki.ubuntu.com/CatalanTeam/Recursos/Versions_Ubuntu](https://wiki.ubuntu.com/CatalanTeam/Recursos/Versions_Ubuntu)

---

### Post by CarlesOriol on 2008-05-02
> **lFossil said:**
> Ei gràcies per l'aclariment, :) he fet el que mas dit, però he posat allò que mas dit al terminal després de fer el de la source list i m'ha sortit això:

jasiel@jasiel-laptop:~$ sudo apt-get update
E: El tipus «[http://archive.ubuntu.com/ubuntu/»](http://archive.ubuntu.com/ubuntu/») no és conegut en la línia 12 de la llista de fonts /etc/apt/sources.list


el **deb** al començament de la linia com t'ha dit en patrick.

---

### Post by lFossil on 2008-05-03
Sí, val ja està merci a tots!!
:lolflag:

---


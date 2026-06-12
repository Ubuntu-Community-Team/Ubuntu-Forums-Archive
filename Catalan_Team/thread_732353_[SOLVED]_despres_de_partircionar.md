---
title: "[SOLVED] despres de partircionar"
date: 2008-03-22
forum: Catalan Team
---

### Post by abosch on 2008-03-22
Hola, 

fa uns dies que vaig fer una instal.lació en un portàtil. Seguint alguns consells qeu vai trobar en el fòrum ( i per algun altre costat), vaig fer  una partició exclusiva per el home (/home) . Així doncs,

/
/swap
/home

Segons tinc entès, el linux funciona d'una manera jeràrquica partint de "/"  .  Tinc un dubte que és : He d'entendre que la partició "/home" està inclosa dintre de la branca "/home" que ja ve en l'estructura de "/" ?  Em sembla que no queda massa clar; vull dir que no veig que tingui cap partició "/home" , el sistema ja la identifica com a particio tot i que la inclou sota de "/" ?

Gràcies, 
Alex

PD. En realitat no van ser 3 les particions sinò 4 , i això ja és un altre post. siau

---

### Post by Neret on 2008-03-22
Si que tens la particio /home. Comprova-ho al menu Sistema/Administracio/Editor de particions
A que tens /dev/sda1/ punt de muntatge /
                 /dev/sda2/                     /swap
                 /dev/sda3/                     /home
I tal com dius segurament tens a la /dev/sda4 /ntfs  :) O no?
salut

---

### Post by abosch on 2008-03-22
ui! efestivament si que la tinc  :) 

de totes maneres, no ho acabo d'entendre;

1. com és que no apareix per llocs->ordinador ?  (i sí l'altra partició i unitat(s))
2. quan guardo música (per exemple) directament  a "/home/usuari/música"  ja va  a la partició ? Vull dir si arribés el dia en que fes alguna cosa que no hauria i que em fes "encallar" el sistema, sempre tindria la partició per recuperar allò guardat?


... l'altre no és nfts , em vaig guardar un espai per provar amb altres distros. 

/
linux-swap
/home
/media/deb



Gràcies, 
Alex

PD. El dubte respecte d'aquesta ultima és: perquè m'hi apareix una carpeta que es diu " lost+found" ?

---

### Post by patrickfromspain on 2008-03-23
No la tens a lloc ordinador, perque forma part del sistema, no es una unitat externa. Efectivament, quan guardes qualsevol cosa a /home/usuari, ho estàs guardant tot en la partició /home, i tens la ventatja de que, arribat el moment, pots formatejar la partcio / i no la home i, per tant, no hi perdries la informacio que hi tens.

salut!

---

### Post by papapep on 2008-03-23
Tal i com ja t'han comentat, el sistema de fitxers és una capa superior a la física dels discs durs. Això permet que quan tu utilitzes la partició que has muntat com a /home, no t'hagis de preocupar de si és la mateixa partició que root (/) o una altra, o un altre disc dur o, fins i tot, un disc dur remot. El sistema operatiu a tu t'ho mostrarà com a una branca més de l'estructura del sistema de fitxers. Curiós, oi? . :-)


EDITO:
Per cert, per si t'interessa, [aquí]("http://extralinux.net/?q=node/6") i  [aquí]("http://extralinux.net/?q=node/30") pots llegir sobre el tema del sistema de fitxers.

---

### Post by CarlesOriol on 2008-03-24
Si ... i nosaltres vam fer un video:-D

[http://www.archive.org/details/Particionant_el_disc_amb_ubuntu](http://www.archive.org/details/Particionant_el_disc_amb_ubuntu)

---

### Post by abosch on 2008-03-25
Gràcies

---


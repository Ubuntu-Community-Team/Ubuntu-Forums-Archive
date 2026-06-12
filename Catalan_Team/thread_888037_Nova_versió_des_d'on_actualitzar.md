---
title: "Nova versió: des d'on actualitzar?"
date: 2008-08-12
forum: Catalan Team
---

### Post by freski on 2008-08-12
Llegint comentaris que la gent deixa per internet sobre l'Ubuntu he vist repetit el tema de les actualitzacions. El que més em va interessar va ser un que deia que és millor actualitzar les versions de l'Ubuntu utilitzant Live CDs i no pas amb el propi gestor d'actualitzacions de l'Ubuntu. No sé massa bé el per què d'aquesta afirmació, i és per això que volia preguntar què en sabeu vosaltres.

Gràcies!

---

### Post by Rubunter on 2008-08-12
Jo tinc el /home en una partició separada i quan toca actualitzar formatejo la partició del / i instal·lo la nova versió des de zero. Recentment un amic va actualitzar a hardy i la configuració de la pantalla es va esconyar. Ho vam solucionar amb l'envy, però algú que no tingui ni fava del tema...crec que amb una cosa així ja hagués tirat la tovallola. La meva recomanació és fer una instal·lació fresca, però això va a gustos.

---

### Post by oriolsbd on 2008-08-13
Jo també sóc partidari d'una instal·lació neta. L'únic problema és que abans t'has d'apuntar tots els programes que tenies instal·lats, i tornar-los a instal·lar en el sistema nou, modificar algunes configuracions, etc. Total, que porta el seu temps.

---

### Post by LitusMayol on 2008-08-13
Jo prefereixo actualitzar desde la xarxa.

He actualitzat de les dues maneres. Però em va agradar més la opció del **Synaptic**. Com diu l'**oriolsbd**per fer l'altra has d'apuntar les configuracions, els programes... Ho trobo una pèrdua de temps. Vaig decidir que una vegada cada 4 actualitzacions en faria una amb LiveCD (perquè així netejo tot el que pugui haver potinejat), però per internet. Sóc un mandres!

PD:**Rubunter**, això del */home* en una partició apart sembla una molt bona idea!

---

### Post by CarlesOriol on 2008-08-13
> **oriolsbd said:**
> L'únic problema és que abans t'has d'apuntar tots els programes que tenies instal·lats...

Jo faig això:

dpkg --get-selections > llista_instala.txt

i sobre el tema de tenir el home separat està bé però tampoc guanyes gaire. Jo sempre tinc una copia en un disc extern del home i em serveix perfectament pels canvis de versions.
L'únic cas que tinc la home separada és en el eee ja que la màquina té una capacitat reduida (4 Gb) i així tinc el home muntat sobre una SD de 4 Gb d'espai pel meu usuari. A l'hora que em serveix per que usant el mateix id d'usuari pugui guardar diferents configuracions de la màquina segons la SD que insereixi abans d'iniciar sessió.

---

### Post by LitusMayol on 2008-08-14
**CarlesOriol**! (ara feia dies que no et veiem per aquí!)

Això:
```
dpkg --get-selections
```
Què fa? Et crea una llista amb el nom "*llista_instala.txt*" i tots els programes instal·lats? (es que si no ho he d'anar apuntant a mà, potser em passo a l'altre bàndol!).

Merci!

---

### Post by CarlesOriol on 2008-08-14
> **LitusMayol said:**
> 
Què fa? Et crea una llista amb el nom "*llista_instala.txt*" i tots els programes instal·lats?

Exacte, després pots recuperar-ho fins i tot amb el synaptic.

Però, cal tenir en compte diverses coses: si l'uses per recuperar una insta&#320;lació del sistema actual llavors collonut, però si el vols usar per actualitzar hauras de repassar el fitxer a ma per evitar que se t'escriguin versions de programes anteriors (on canvii el nom i no sols el nombre de la versió com els controladors, el kernel, el python o el postgres.)

---

### Post by LitusMayol on 2008-08-14
Huaré de fer una samarreta com les de NY, però:
```
[CENTER]**I** [COLOR="Red"](COR)[/COLOR]
**CarlesOriol**[/CENTER]
```
hehe!xD

Fantàstic! Doncs ja m'ho miraré, però t'asseguro que és més ràpid i més que còmode que fent-ho a mà, com ho feia quan volia "*netejar*". 

Merci mestre!

---

### Post by Rafel HiR on 2008-08-16
Jo q sóc nou en este món de Linux,tinc Ubuntu, el q tinc és una carpeta compartida amb el meu Pc de windows, i si he de formatar, q ja ho he fet perquè al principi em dedicava a mirar, tocar, experimentar..., ho passe a Windows(encara q hi han coses q no guarde perquè tinc la còpia de suport a Win). Una instal·lació fresqueta i passe de nou els fitxers.De reinstal·lar programes, m'és igual, digam q segons els vaig necessitant, els vaig instal·lant i au.
És la cosa bona de tindre la Vídeoconsola XP. Em val per a jugar a "jocs clàssics" i com a magatzem,hehehe.

---

### Post by Ferri on 2008-08-16
Sempre és una bona idea fer una còpia de seguretat abans de fer res, però com ja han dit més amunt, si tens la precaució de posar la teva "home" en una partició separada i no la formates quan fas una instal·lació "nova", no hi ha cap necesitat d'anar copiant els fitxers d'un lloc a l'altre. A més, això no només et conserva els teus fitxers personals, també podràs mantenir les configuracions que hagis fet del teu escriptori i dels diferents programes que tinguis. Cal tenir en compte que si havies triat, posem per cas, un estil d'escriptori que no t'has instal·lat a la nova versió, aleshores no ho veuràs com abans fins que el reinstal·lis (fent servir la llista que tens gràcies a la recomació del CarlesOriol).

---

### Post by Daerun on 2008-08-16
Ostres, això sí que és interessant, i com es pot fer per passar la Home a una altre lloc?

---

### Post by Rafel HiR on 2008-08-16
Però jo sóc molt inexpert. Sóc un nou vingut,hehehe, i no ser fer eixes coses tan avançades :P.
I ja q estem:
Com es fa això d'instal·lar el Home en una altra partició?

---

### Post by patrickfromspain on 2008-08-17
per instal·lar el home en una altra particio, quan arribeu a l'hora de definir particiones, heu de crear la particio amb punt de muntatge /, una altra amb muntatge a /home i a part, la swap.

Salut

---

### Post by Daerun on 2008-08-22
De manera que només es es pot fer en una instal·lació nova?

---

### Post by papapep on 2008-08-23
No, també es pot fer en un sistema ja instal·lat, però porta molta més feina i és més delicat. Canviar la distribució interna d'un pis és molt més fàcil quan encara no s'han aixecat els envans que un cop ja s'hi està vivint, oi? :-)

---

### Post by patrickfromspain on 2008-08-23
com diu en papapep es pot fer. A grosso modo, el que vaig fer jo va ser:


Redimensionar la meva particio d'ubuntu al minim possible
Crear una nova particio
Moure /home a /home2
Copiar tot el que hi havia a /home2 a la particio nova
Crear /home
Editar l'fstab per fer que la nova particio es munti a /home. La meva linia d'fstab diu: /dev/sdb2  /home   ext3   relatime    0   2
Reiniciar i resar :D
Si tot es correcte i no et falta res, borrar /home2

Ves amb compte, igual no es exacte. Si et fa por quedar-te en busybox, millor no ho facis. Si no recordo malament, el meu ubuntu era a la particio sdb1, i al fer-ho vaig especificar com a /home sda2 i va fallar, i em sembla que vaig anar a parar a la pantalleta negra en plan ms-dos. Ho vaig poder solucionar tot sense massa problemes, però clar, t'has de sentir mes o menys comode en aquell entorn.

salut

---


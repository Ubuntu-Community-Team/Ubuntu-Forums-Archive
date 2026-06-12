---
title: "Disc dur nou"
date: 2008-09-07
forum: Catalan Team
---

### Post by venusfenix on 2008-09-07
Bon dia,

un nou tema, he estat buscant pero no he trobat solucio.
he comprat un segon disc dur pel meu portatil, pero no hi ha manera de formatajar-lo i fer-lo servir com una unitat de fitxer d'usuari.

tinc instalat el SDM i el gparted, pero no m'entero.

Gracies,

---

### Post by papapep on 2008-09-07
Intern o extern?

> no hi ha manera de formatajar-lo i fer-lo servir com una unitat de fitxer d'usuari.

tinc instalat el SDM i el gparted, pero no m'entero.

Què es l'SDM?
Què has provat que no et funcioni?
T'apareix al gparted?

---

### Post by venusfenix on 2008-09-07
el disc dur es intern.
L'SDM = storage device manager
tinc instalat el gparted, pero desconec com tinc que fer-ho...
he provat amb ext3, pero despres, tinc disc dur, no esta muntat, i no puc crear carpetes.... 
que tinc que fer??

gracies,

---

### Post by papapep on 2008-09-07
> el disc dur es intern.

Ja sabem alguna cosa.

> L'SDM = storage device manager

Ah....no l'he fet servir mai...

> tinc instalat el gparted, pero desconec com tinc que fer-ho...

Doncs fer-te un manual aquí és complicat :-), més quan a internet n'hi ha a palades. Fent una [simple búsqueda a google]("http://www.google.es/search?hl=es&q=manual+de+gparted&btnG=Buscar+con+Google&meta=") 

> he provat amb ext3, pero despres, tinc disc dur, no esta muntat, i no puc crear carpetes....

...si no està muntat, evidentment, és com si no el tinguessis.
Et cal decidir quin punt de muntatge li vols assignar: /home, /usr/bin, /home/armari, /home/jo/dades....el que vulguis.

Un cop ho hagis fet, crees el directori si no existeix, i afegeixes la línia corresponent a /etc/fstab.

> que tinc que fer??

Doncs com que, pel que sembla, ja has particionat el nou disc i creat el sistema de fitxers (en aquest cas EXT3), només et queda el que t'he comentat del punt de muntatge i l'fstab.

---


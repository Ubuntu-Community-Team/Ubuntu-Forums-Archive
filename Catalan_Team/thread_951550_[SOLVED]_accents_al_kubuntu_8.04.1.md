---
title: "[SOLVED] accents al kubuntu 8.04.1"
date: 2008-10-18
forum: Catalan Team
---

### Post by carles67 on 2008-10-18
Bon dia a tothom.

He instal·lat un kubuntu 8.04.1 al portatil Toshiba satellite A210-158 Turion 64 x2 dual core i em trobe que al posar els accents i voler escriure "í" amb l'openoffice , kword o kate em  posa "i´" i així totes les vocal accentuades. El País posat és espanya i la llengua és el català. 
Si vaig a "Arranjament de sistema" i mire "Disposicó del teclat" no tinc res activat però si ho active no tinc resultat millor doncs el teclat d'aquest model de portàtil no hi és.

Que puc fer ?

---

### Post by carles67 on 2008-10-18
Ja ho he trobat com arreglar-ho cercant per google. 	](*,)
Cal anar a K, sistema . consola, i mirar la llengua per defecte posant "locale" sense les cometes i prement enter.
Si la llengua és ca_ES.UTF-8@valencia cal canviar la llengua posant a la consola "sudo kate /etc/default/locale" sense les cometes i canviant la línia
ca_ES.UTF-8@valencia
per 
ca_ES.UTF-8
Reiniciar l'ordinador.

Disculpeu que m'haja posat nerviós i us haja preguntat abans de perdre una estona cercant per google, però ho havia remenat tot i no veia on estava la errada.
Salutacions. :guitar:

---


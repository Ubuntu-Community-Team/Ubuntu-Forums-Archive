---
title: "visualització incorrecta d'accents a la terminal"
date: 2008-06-03
forum: Catalan Team
---

### Post by borgg on 2008-06-03
Salut amic ubuntaires!

Tinc un problema que és insignificant però el tinc des del principi d'usar l'ubuntu i em fa mola ràbia, si em podeu donar un cop de ma us ho agrairé molt!

El problema és que des de la gnome-terminal veig els accents perfectament, però si faig control+alt+F1 per canviar de l'entorn gràfic a mode terminal no puc veure els accents ni els caràcters catalans,

Algú se li acut d'on pot provenir aquest problema i com solucinar-lo?

Moltes gràcies ja d'avançat

PD: uso ubuntu 8.04 però des del feisty amb el que vaig començar m'ha passat sempre aquest problema :(

---

### Post by trinkus on 2008-06-04
No se si te a veure pero el paquet d'idioma catala d'andorra a mi em donava problemes d'aquest tipus, per exemple, amb el Kile. Vaig fer servir el catala d'Espanya (una mica incoherent.... pero...) i ja va anar tot be...

---

### Post by papapep on 2008-06-04
Quan fas al terminal:

```
locale
```

què et surt?

---

### Post by borgg on 2008-06-04
salut!

doncs aviam, el paquet d'idioma és el català d'espanya :S

i si fico locale coincideix amb el del gnome-terminal; tot està amb utf8 (adjunto el comando locale)

```

LANG=ca_ES.UTF-8
LC_CTYPE="ca_ES.UTF-8"
LC_NUMERIC="ca_ES.UTF-8"
LC_TIME="ca_ES.UTF-8"
LC_COLLATE="ca_ES.UTF-8"
LC_MONETARY="ca_ES.UTF-8"
LC_MESSAGES="ca_ES.UTF-8"
LC_PAPER="ca_ES.UTF-8"
LC_NAME="ca_ES.UTF-8"
LC_ADDRESS="ca_ES.UTF-8"
LC_TELEPHONE="ca_ES.UTF-8"
LC_MEASUREMENT="ca_ES.UTF-8"
LC_IDENTIFICATION="ca_ES.UTF-8"
LC_ALL=

```

el més curiòs del tema és que si estic al gnome-terminal tot va bé, però si entro a la terminal de ctrl+alt+F1, no em deixa ficar accents i enlloc d'imprimir-se'm la lletra ñ surt un símbol amb moltes ralles blanc i pràcticament quadrat, molt extrany totplegat

algú se li acut a que pot ser degut? no tinc ni idea del que fer :S

gràcies!!!

---

### Post by borgg on 2008-06-04
sembla ser que aquest és un bug d'ubuntu :S

[https://bugs.launchpad.net/ubuntu/+source/console-tools/+bug/29523](https://bugs.launchpad.net/ubuntu/+source/console-tools/+bug/29523)

podeu escriure accents vosaltres quan us trobeu a la terminal tty1 (ctrl+alt+F1)?

---

### Post by papapep on 2008-06-04
Si fas a un terminal (o a un tty, clar):

```
sudo dpkg-reconfigure console-setup
```

podràs seleccionar el teclat, l'idioma, la codificació "ISO-8859-15" i, finalment, seleccionar "Latin1 and Latin5 - western Europe and Turkic languages".
Un cop fet això, podràs posar accents als tty's, ni que sigui d'una manera una mica precària, ja que hauràs de prémer l'accent, la lletra a accentuar i espai per a que es vegi el caràcter, però funcionarà.

AFEGITÓ: Per cert, et funciona correctament amb el gnome-terminal perquè les locale a Gnome es configuren a nivell de servidor gràfic, fet que no passa amb les tty.

---

### Post by borgg on 2008-06-05
Gràcies papapet!

Ets tota una biblia oberta del programari lliure :D

Per cert, el que no entenc és perquè les consoles virtuals no funcionen amb codificació de caràcters utf8, hauria de funcionar no?

és que ho veig molt xapusses treballar amb una consola amb codificació ISO-8859-15, això pot donar errors si s'està treballant amb un document que l'has editat amb aquesta codificació i després hi treballes amb la ut8 des de l'entorn gràfic.

de totes maneres gràcies novament! alemnys ja puc visualitzar els accents

---

### Post by borgg on 2008-06-10
hola de nou papapep,

ara ja puc ficar els accents però m'ha passat el que em temia, el sistema no em visualitza bé els missatges perquè segurament els tregui amb una altra codificació de caràcters

per exemple, al introduir a la terminal aquest codi
```
cat hola > hola

```
em surt un missatge d'error amb els accents il·legibles :S

quin rotllo aquest tema, tu saps perquè la terminal no soporta utf8 directament?

gràcies de nou!!

---


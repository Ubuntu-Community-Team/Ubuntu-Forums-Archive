---
title: "[SOLVED] wifi no funciona amb kernel 2.6.24.16"
date: 2008-08-14
forum: Catalan Team
---

### Post by miquelet on 2008-08-14
Tinc un portàtil hp pavillion dv6000. Hi tenia l'ubuntu 7.10, que em reconeixia la tarja wifi.  Fa unes setmanes vaig decidir actualizar-lo amb Hardy.  Des de llavors que no em reconeix la tarja wifi.  El cas és que si arrenco el sistema amb l'opció del kernel 2.6.22.14 em reconeix la tarja wifi sense problemes.  La tarja és una broadcom.  Agrairia que m'orientéssiu una mica i m'expliquéssiu per què em passa això.  Moltes gràcies.

---

### Post by torracastanyes on 2008-08-14
He vist que parlen d'aquest tema aquí:

[http://www.ubuntu-es.org/index.php?q=node/95609](http://www.ubuntu-es.org/index.php?q=node/95609)

---

### Post by miquelet on 2008-09-16
He visitat la pàgina que em deies i he fet tot el que se'm proposa, però no hi ha manera.  Si la solució és instal·lar b43-fwcutter, jo ja ho he fet i tot i amb això, no em detecta la tarja.  Algun suggeriment companys?

---

### Post by jaume69 on 2008-09-18
[[COLOR="Red"]Aquí[/COLOR]]("https://bugs.launchpad.net/linux/+bug/176090") hi ha una persona(LucaScarpantonio) que ho ha resolt instal.lant,**linux-backports-modules-hardy**

No deus pas tenir 64 bits,de processador.

Mira si la iw- és la mateixa que pose a dalt,a la web de Launchpad.

No sé..

---

### Post by miquelet on 2008-09-19
Problema resolt!  Vaig decidir instal·lar de nou la Hardy; vaig fer l'actualització corresponent.  Llavors vaig anar al Synaptic i vaig buscar el b43-fwcutter.  Mentre feia això, la màquina em va avisar que hi havia nous controladors disponibles per a la tarja wifi broadcom.  El vaig instal·lar i, voilà.  Gràcies!

---


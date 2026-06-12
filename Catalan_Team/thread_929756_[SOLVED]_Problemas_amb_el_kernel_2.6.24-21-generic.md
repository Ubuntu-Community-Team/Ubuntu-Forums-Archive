---
title: "[SOLVED] Problemas amb el kernel 2.6.24-21-generic"
date: 2008-09-25
forum: Catalan Team
---

### Post by tanreb20 on 2008-09-25
Hola!

Desde que vaig instalar aquest kernel **2.6.24-21-generic** tinc cantitat de problemas.

L'audio no em funcionava, pero reinstralant l'alsa a la ultima versio estable ho vaig solucionar.

El problema ara el tinc amb el wifi, al lspci si que el detecta, i tinc el ndiswrapper amb el driver instalat pero no va... El NetworkManager no reconeix la tarjeta.


```
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

Alguns programes fallen xq si (segmentation fault) quan volen.

Diria que per ara aixó és tot, pero el més problematic és lo del wireless.

Ho he provat amb intrepid i detecta la tarjeta i les xarxes pero no s'hi conecta ni pá atrá

---

### Post by jaume69 on 2008-09-25
Jo un dia vaig intentar instal.lar un Kernel a **Feisty** i em van caure els "collons" a terra...,ja no dic més.
 
Crec que és més per a experts,aquests tipus d'instal.lacions.

Merci.

---

### Post by patrickfromspain on 2008-09-25
Desinstal·la'l. Hauries d'estar fent servir el kernel 2.6.24-19-generic. El problema es que deus tenir activat el repositori hardy-proposed, que es un repositori de prova, amb versions en desenvolupament. Jo el que faria es desinstal·lar aquest kernel i tornar al -19-generic i desactivar el repositori hardy-proposed

salut

---

### Post by tanreb20 on 2008-09-25
juer...

Ja he posat el kernel 19.

Pero no hi ha manera, la wifi segueix sense rular, i la webcam no apareix per enlloc... no s'engega i avans anava.

amb el kernel 20 m'havia funcionat tot, l'instalo?

---

### Post by patrickfromspain on 2008-09-25
anteriorment, t'havia funcionat amb el kernel -19? O amb el -19 mai t'ha funcionat?

D'altra banda, si el -20 no t'ha donat problemes, encara que sigui un kernel de desenvolupament, no hi ha problema en fer-lo servir, si et funciona be.

salut

---

### Post by tanreb20 on 2008-09-25
Ja esta!!!

El kernel 20 es el millor! jajjaja

(Com sabeu q esta en desenvolupament?)

L?unic que pasa es q ara el update-manager em diu que no pot actualitzar xq em fa una actualitzacio parcial o no se q... i no puc fer res amb allo, i la fletx avermella don amolt de mal rollo!

---

### Post by patrickfromspain on 2008-09-25
si tens el kernel -20 instal·lat i et funciona tot be, jo el que faria es desactivar el repositori hardy-proposed i fer un sudo apt-get update.

salut

---

### Post by tanreb20 on 2008-09-25
Ja esta solucionat!

He instalat el kernel 20 i  em va tot perfecte!

L'unic prioblema que tinc ara és amb el router.. no se xq el wifi no funciona les conexions HTTP pero els pings si....

---


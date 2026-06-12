---
title: "Sessió remota gràfica"
date: 2008-08-16
forum: Catalan Team
---

### Post by anigwei on 2008-08-16
Hola,

Sempre he tingut un servidor a casa però hi he entrat en local i remotament via SSH. Ara en tinc un però sense monitor ni teclat, i m'interessaria poder entrar-hi gràficament a banda de SSH. Li he posat XUbuntu, per tant no té "de sèrie" el servidor VNC del Gnome (Vinagre?).

He provat l'X11VNC, però el problema és que al iniciar-se les X, al no detectar monitor, es posa en mòde 640x480 i d'aquí no el mous.

Alguna idea/suggerència? Gràcies!!

---

### Post by papapep on 2008-08-16
Doncs depèn de què pretenguis fer exactament en connectar-te. 
M'explico, si només vols fer anar alguna aplicació concreta (no gaire pesada) i puntualment per administrar algun servei, igual un simple X forwarding per SSH ja et serveix (exportar l'aplicació al teu escriptori). 

Si és alguna cosa més contundent o continuada (p. ex. fer servir l'escriptori del teu servidor com si fos local) doncs igual et farà falta configurar-te un servidor FreeNX, que és el més ràpid que he vist per servir sessions gràfiques remotes.

---

### Post by anigwei on 2008-08-16
Papapep, fa molt bona pinta això del FreeNX, no ho coneixia.

Gràcies per la informació, m'ho miraré!

---

### Post by CarlesOriol on 2008-08-17
Amb ssh -X inicies un terminal que pots obrir aplicacions gràfiques remotes, però consumeix més ample de banda que el freenx que et diu en papapep.

El servidor vnc en gnome es diu vino. (i... d'aquí la gracieta de posar al client vinagre).
Una altra opció en vnc és el tightvncserver-

---


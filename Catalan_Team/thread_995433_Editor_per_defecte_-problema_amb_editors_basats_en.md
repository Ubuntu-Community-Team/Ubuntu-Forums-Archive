---
title: "Editor per defecte -problema amb editors basats en xterm"
date: 2008-11-27
forum: Catalan Team
---

### Post by antoni2 on 2008-11-27
Tinc el Xubuntu 8.10 instal.lat.
Normalment uso l'Emacs o el mousepad per editar. Pero de vegades m'gradaria un editor mes lleuger i mes rapid d'0brir-se que l'emacs, i amb més opcions que el mousepad. 

He provat de  configurar l'editor per defecte (el que s'obre quan cliques un fitxer), però sols funciona pels editors no basats en xterm. O sigui, se m'obre be quan l'editor es Emacs, o Vim, pero no quan intento obrir-los amb joe o zile. (tot i que aquests programes se m'obren be si dono la ordre des del terminal). Què passa?

He provat fer  

sudo update-alternatives --config editor

pero no funciona.  També he putinejat una mica les opcions del terminal (Terminal, emulador de xterm de xfce) i he provat també posantt com a terminal el Konsole, pero res.

Alguna idea ?

Gracies.

---

### Post by papapep on 2008-11-28
No crec que programes que no saben parlar directament amb el servidor gràfic (que no fan servir llibreries que hi parlin) es puguin executar com tu vols.

---

### Post by antoni2 on 2008-11-30
Ja podria ser. De totes formes no hauria de ser tan dificil, oi?

---


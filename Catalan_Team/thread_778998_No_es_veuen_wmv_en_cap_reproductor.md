---
title: "No es veuen wmv en cap reproductor"
date: 2008-05-02
forum: Catalan Team
---

### Post by lFossil on 2008-05-02
Ja fa fies que no se què hi passa i no trobo el que és que no puc reproduir vídeos wmv en cap programa. El que passa es que es posa la pantalla en negre i a voltes surt la imatge durant menys d'un segon i es torna a esvair, però el so funciona correctament.
He provat amb altres programes per reproduir audio però tots em fan el mateix!   :confused:

---

### Post by papapep on 2008-05-02
Tens els efectes d'escriptori activats? Has provat a desactivar-los?

---

### Post by lFossil on 2008-05-02
Sí, es veritat, sí que funciona.
Així mentre tingui activats els efectes d'escriptori no podré veure vídeos?
O hi falla alguna cosa?


Merci!!

---

### Post by CarlesOriol on 2008-05-02
És probable que no puguis fer res més.

Però prova el xine.

---

### Post by niculau on 2008-05-03
prova a canviar el modul de sortida a X11 en el cas del VLC.

---

### Post by LitusMayol on 2008-05-09
> Tens els efectes d'escriptori activats? Has provat a desactivar-los?

Perquè no funcionarà si té els efectes d'escriptori activats? No hi ha cap manera de que pugui fer ambdós coses?(És curiositat)

---

### Post by orestesmas on 2008-05-09
Probablement sí que et funcionarà, però com bé apunta niculau (encara de forma críptica) un programa té diverses maneres de presentar la seva sortida per pantalla (i en el cas de vídeo en moviment la cosa es complica). Hi ha algunes d'aquestes maneres que són compatibles amb OpenGL (que és allò que usen els efectes d'escriptori) i altres que no ho són. Has de cercar alguna opció de configuració del teu reproductor de vídeo que et permeti canviar el "driver de sortida" de vídeo. Prova diverses opcions (XShm, xv, X11...) perquè jo no em sé de memòria quines són les compatibles.

---

### Post by RainCT on 2008-05-11
No sé ben bé per a que serveix, però prova també d'insta&#320;lar el compizconfig-settings-manager i llavors a Sistema > Preferències -> Configuració avançada dels efectes d'escriptori assegura't que a l'apartat Utility hi tinguis l'opció «Video Playback» activada, a veure si amb això aconsegueixes que funcioni.

---


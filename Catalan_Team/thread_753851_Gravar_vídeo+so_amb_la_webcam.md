---
title: "Gravar vídeo+so amb la webcam"
date: 2008-04-13
forum: Catalan Team
---

### Post by pespin on 2008-04-13
Bones,

algú em sabria dir d'algun programa que gravi vídeo amb so (via micròfon separat de la càmera) fàcilment?

Els pocs programes que capturen vídeo que he trobat no capturen so o no sé com fer-ho.

Ja que hi estem m'agradaria saber si hi ha cap manera per a dir que carregui la cam a /dev/video0 i no a /dev/video1 (a /dev/video0 actualment tinc una targeta de TV que no em funciona). És a dir, m'agradaria intercanviar els noms de dispositiu, perquè hi ha programes que agafen el /dev/video0 predeterminadament i d'altres com el cheese que no em deixen triar altres dispositius.

---

### Post by pespin on 2008-04-15
Ostres 2 dies i cap resposta, on s'ha vist això?! :lolflag:

Ningú té ni idea del tema de webcams? >.<

---

### Post by Joan Marc on 2008-04-15
L'únic que sé és que amb això, ubuntu té molta i molta feina xD
A mi ni me la detecta](*,)

---

### Post by jaume69 on 2008-04-15
Carai..!!,si que demanes tu.
Jo,tan sols pogués gabar un video amb una mica de música,JA SERIA MOLT!!!!
jajajaja.

Entre altres................................................................................

P.D.Tot i que critico Ubuntu,Linux,Gnu/Linux,....,tampoc amb Windows(Vista) és que sigui gens fàcil fer un vídeo amb so.

---

### Post by jaume69 on 2008-04-19
Doncs res,que quan vull configurar el so per grabar em surten aquests missatges...

Ara hi tinc** PulseAudio** pero tant amb** Alsa Mixer** com amb **Oss Mixe**r,em diu el mateix.

:guitar:

---

### Post by pespin on 2008-04-19
De moment l'única aplicació que he conseguir fer funcionar amb la webcam (dispositiu V4L1) per a gravar so i vídeo és l'aplicació 'streamer' amb la ordre següent:

```
streamer -q -c /dev/video1 -f rgb24 -r 25 -t 00:30:00 -o clip.avi -F stereo
```

Seguiré informant-me sobre els paràmetres del programa per treure'n més profit i buscant d'altres aplicacions més amigables, a poder ser amb GUI.

PD: per instal·lar streamer... sudo aptitude install streamer

---


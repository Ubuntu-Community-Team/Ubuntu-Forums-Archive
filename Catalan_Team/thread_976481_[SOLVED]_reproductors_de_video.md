---
title: "[SOLVED] reproductors de video"
date: 2008-11-09
forum: Catalan Team
---

### Post by muleta on 2008-11-09
L'intrepid no em reprodueix la imatge, només el so, en tots els reproductors de video.

He reinstal·lat el vlc, l'he eliminat totalment i l'he tornat a instal·lar, he provat el Totem, el Gnome Media Player, etc. Amb tots fa igual. I també amb les targetes de les càmeres de video. 

Què li deu passar?.

---

### Post by SiscoGarcia on 2008-11-09
Hola muleta, no tinc gaire idea de vídeo però potser que el problema es degui als còdecs que tens instal·lats. Si el format és privatiu i no hi has fet res, potser que et calgui instal·lar els ubuntu-restricted-extras des de consola fent:

```
sudo apt-get install ubuntu-restricted-extras
```

ja diràs si és això.

---

### Post by muleta on 2008-11-09
Es veu que no perque em respon que "ubuntu-restricted-extras ja es troba en la versió més recent" i no em canvia res.

---

### Post by CarlesOriol on 2008-11-09
Probablement és un problema a l'overlay de la gràfica.

Quina gràfica tens i quin controlador ?

Has provat deshabilitant els efectes d'escriptori?

---

### Post by muleta on 2008-11-09
Estic fent tota mena de maniobres.

He desinstal·lat l'EnvyNG i l'he tornat a instal·lar.

Tinc l'ATI T.I.R XPRESS 200 M 5955 (PCIE) i l'Envy m'ha instal·lat un control·lador semblant i recomanat, però que no és el d'aquest model.

Ara veig i sento el video però no em funciona el sò a l'Skype.

No tinc activats els efectes d'escriptori.

---

### Post by muleta on 2008-11-12
> **muleta said:**
> Estic fent tota mena de maniobres.
 
He desinstal·lat l'EnvyNG i l'he tornat a instal·lar.
 
Tinc l'ATI T.I.R XPRESS 200 M 5955 (PCIE) i l'Envy m'ha instal·lat un control·lador semblant i recomanat, però que no és el d'aquest model.
 
Ara veig i sento el video.
 
 
 
Donat que es reprodueix el video, amb aquesta reinstal·lació de l'EnvyNG i l'instal·lació del control·lador recomanat, podem dir que el tema està resolt.

---


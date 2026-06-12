---
title: "Els Videos surten en Blanc i Negre"
date: 2007-11-24
forum: Catalan Team
---

### Post by ernestux on 2007-11-24
Hola a tothom,

Fa 2 setmanes que vaig fer el canvi a ubuntu GUTSY; tot perfecte; els reproductors de videos (totem, vlc, mplayer) em fan les imatges més allargades del normal. 
Avui no sé que ha passat que es veuen els videos (.mov , .ogg , .avi) en tots els reproductors en BLANC I NEGRE !  Suposo que és de fàcil arreglo , per això us demano ajut.

Les fotografies, icones i pantalla sí que surt en color.

Gràcies

---

### Post by CarlesOriol on 2007-11-24
quina gràfica tens?

---

### Post by ernestux on 2007-11-25
> **CarlesOriol said:**
> quina gràfica tens?

Intel 915 GM , en un portàtil.
Aquest matí ja es veien en color. No sé, la meva filla havia tocat coses abans....
Ara tornen en blanc i negre. Què podria  mirar?
Uso el motor gstreamer.
I he vist, que els videos de youtube sí que es veuen en color.

Gràcies,

---

### Post by papapep on 2007-11-25
> Es podria suprimir aquest post, perquè no aporta res,doncs.

Nooo, això no és veritat...ha estat un exemple més de que els ordinadors (com a mínim els dels grans) no són una joguina pels nens :-D

---

### Post by ernestux on 2007-11-27
Hola de nou,

He trobat aquesta informació referida a la placa INTEL, :
This post could be related to an Ubuntu bug filed at: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/149791](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/149791)

He provat aquesta comanda:  "rm -r ~/.gconf/apps/totem" , i he fet logout i login un altre cop , i m'ha aparegut el color en els videos .

Altres ho solucionen: 
gstreamer-properties -> Video -> Output -> X Window System (No Xv)

Amb el totem gstreamer segueix allargant la imatge, però. En totem-xine he vist que no.

Gràcies

---


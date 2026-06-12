---
title: "Problemas con archivos .MP4"
date: 2008-10-17
forum: Centroamerica Team
---

### Post by meldon12 on 2008-10-17
Hola chicos, tiempo yo de no postear aqui xD, pero bueno lamentablemente no tengo excusas q darles jeje.

Bueno mi problema es que ya he podido reproducir todo bn respecto a archivos avi y algunos mp4 q no tienen el codec h/x264, cuando intento reproducir este ultimo, al principio solo se reproducia horrible, pero luego lo abria y el reproductor se cerraba, ya sea el VLC o el Totem, el mplayer siemrpe me manda este error con cualquier archivo "Error opening/initializing the selected video_out(-vo) device."

No se proq sera, agradeceria cualquier ayuda. muchas gracias a todos de antemano.

saludos

meldon12

---

### Post by meldon12 on 2008-10-19
he logrado reproducir mp4 con el mplayer, entre en prefrencias>>>video>> y en "Available drivers" escogi gl2, pero aun asi lo reproduce demasiado lento, nose q hacer he leido por todos lados, quiero verlo aqui en ubuntu nada de windows plss ayudaa

saludos

meldon12

---

### Post by srlinux on 2008-10-24
> **meldon12 said:**
> he logrado reproducir mp4 con el mplayer, entre en prefrencias>>>video>> y en "Available drivers" escogi gl2, pero aun asi lo reproduce demasiado lento, nose q hacer he leido por todos lados, quiero verlo aqui en ubuntu nada de windows plss ayudaa

saludos

meldon12

hola te recomiendo que instales el **ubuntu-restricted-extras** y el **W32 Codec** con eso podras ver tus mp4 si problemas y de reproductor el **VLC**

```
sudo apt-get install ubuntu-resricted-extras
```
W32 Codecs &#8594; [http://srinuxubuntu.homelinux.com/index.php/w2-codec/](http://srinuxubuntu.homelinux.com/index.php/w2-codec/)

---

### Post by meldon12 on 2008-10-27
el problema no es que no tenga los codecs, eso ya lo he hecho, lo que digo es que lo que no reproduzco son los archivos mp4, todo lo reproduuzco bien porq hacer raaato baje los restricted y los w32codecs.

Igual muchas gracias por contestar, porq despues dicen en el mail que uno no usa los forosy mira, nadie conectesta.

saludos

---

### Post by meldon12 on 2008-11-11
Ya lo he arreglado, con el mplayer, me fui a Preferences>>Video>>>X11(XImage, Shm) y en Audio escogi el alsa, pero ahora hay otro problema xD, q aveces le mplayer no inicializa el dirver de sonido, cuando me voy a Sistemas>>Preferencias>>Sonido (menu ubuntu) y pongo en probar el audio, me dice q el dispositivo lo esta usando otra aplicacion, y segun he leido, es porq linux utiliza la tarjeta de sonido q tengamos de la menra correcta, osea, en una sola aplicacion, el problema es q no se q aplicacion es la q se queda usando el sonido y no me deja usraklo en las demas jaja.

bueno saludos a todos

m3ld0n

---

### Post by eivar on 2008-11-12
Hola meldon yo tenía un problema parecido con el sonido en Feisty, lo que hice lo puedes ver [aquí.]("http://ubuntuforums.org/showthread.php?t=807406")

Saludos.

---

### Post by meldon12 on 2008-11-12
otra vez, gracias por la ayuda eivar, quien pensaria q la solucion era tan simple xD

saludos

---

### Post by eivar on 2008-11-12
¿Cual era la solución?

Saludos.

---

### Post by meldon12 on 2008-11-14
disculpa eivar las gracias eran para ti, es q confundo a mayeco y a ti, no se porq xD, disuclpame y gracias en serio.

saludos

---

### Post by eivar on 2008-11-14
:popcorn: Ok no hay problema.

Saludos.:lolflag:

---


---
title: "Vostro 1400 How to set the mic jack as output?"
date: 2010-10-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gabrielbecker on 2010-10-23
Vostro 1400 has 3 jacks, 2 for headphone and 1 for mic. On windows, i can set the mic jack as output and i can have a 5.1 sound, but on ubuntu i'm not able to set that jack as output. I've tried the alsamixer, but there i can only choose between 'mic in' and 'line in'. And in the sound mixer, i can choose only between 2 2.0 outs and 1 mic in, or one 4.0 sound and a mic in.
Is there any way to 'fix' it, to set de mic in as out and have a 5.1 sound?
This can be usefull:

gabriel@gabriel:~$ aplay -l
**** Lista de Dispositivos PLAYBACK Hardware ****
placa 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Dispositivo secundário: 0/1
  Dispositivo secundário #0: subdevice #0
placa 0: Intel [HDA Intel], dispositivo 1: STAC92xx Digital [STAC92xx Digital]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0

gabriel@gabriel:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

gabriel@gabriel:~$ head -n 1 /proc/asound/card0/codec#0
Codec: SigmaTel STAC9228

gabriel@gabriel:~$ head -n 1 /proc/asound/card0/codec#1
Codec: Conexant ID 2c06

Sorry for my english:)

---


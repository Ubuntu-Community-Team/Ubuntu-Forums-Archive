---
title: "Sense audio (ni analògic ni digital)"
date: 2008-11-29
forum: Catalan Team
---

### Post by vinga on 2008-11-29
Hola, m'he comprat una tele que té s/pdif (Sony/Philips Digital Interface Format), he connectat el cable al pc (tarja de so integrada ALC822) i no tinc so.
També hi he connectat els altaveus amb el jack normal, i tampoc funciona.
Amb windows no he provat el digital encara, però l'analògic si que va.

Deixo això per si serveix d'alguna cosa:

> grig@grr:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


> grig@grr:~$ ls -la /proc/asound/
total 0
dr-xr-xr-x   5 root root 0 2008-11-29 10:40 .
dr-xr-xr-x 159 root root 0 2008-11-29 09:35 ..
dr-xr-xr-x   7 root root 0 2008-11-29 11:54 card0
-r--r--r--   1 root root 0 2008-11-29 11:54 cards
-r--r--r--   1 root root 0 2008-11-29 11:54 devices
lrwxrwxrwx   1 root root 5 2008-11-29 11:54 Intel -> card0
-r--r--r--   1 root root 0 2008-11-29 11:54 modules
dr-xr-xr-x   2 root root 0 2008-11-29 11:54 oss
-r--r--r--   1 root root 0 2008-11-29 11:54 pcm
dr-xr-xr-x   2 root root 0 2008-11-29 11:54 seq
-r--r--r--   1 root root 0 2008-11-29 11:54 timers
-r--r--r--   1 root root 0 2008-11-29 10:40 version
grig@grr:~$ 



Edito: he trobat això [http://www.cs.tut.fi/~ik/mpegspdif.html](http://www.cs.tut.fi/~ik/mpegspdif.html) però no ho sé instal·lar.

Gràcies!

---


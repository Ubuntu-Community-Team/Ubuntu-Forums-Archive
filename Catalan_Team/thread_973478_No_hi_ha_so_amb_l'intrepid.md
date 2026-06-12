---
title: "No hi ha so amb l'intrepid"
date: 2008-11-06
forum: Catalan Team
---

### Post by bonpartit on 2008-11-06
Bones,

He installat la versio 8.10 i no hi ha manera de fer funcionar el so, tinc un portatil ben normalet pero no hi ha manera

rosle@robert:~$ cat /proc/asound/cards
 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1981B at irq 21

Aqui hi ha els detalls de l'escript alsa-info.sh que dona l'informacio de la configuracio de so:

 [http://www.alsa-project.org/db/?f=7f35b282e26c0ba95a210f9ebc36ceaeaf6589e8](http://www.alsa-project.org/db/?f=7f35b282e26c0ba95a210f9ebc36ceaeaf6589e8)

Espero que algu tingui una pista

Salutacions

---

### Post by bonpartit on 2008-11-06
mes detalls...

rosle@robert:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
rosle@robert:~$

---


---
title: "Audio 82801I (ICH9 Family) HD Audio Controller"
date: 2011-10-12
forum: Desktop Environments
---

### Post by giogiomogio on 2011-10-12
Hi
I'm a ubuntu (11.04) member of the italian community.
I'm here because i have a problem not solved in the italian community and maybe, here, i will fix it.

I have a pc desktop,
motherboard: intel dp35dp
Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02) 

the problem is that i have the perfect sound on back jack but not in front jack....(i feel nothing).
In the alsamixer the situation is:
[http://forum.ubuntu-it.org/index.php...h=117369;image]("http://forum.ubuntu-it.org/index.php?action=dlattach;topic=484222.0;attach=117369;image")
bios situation is:
[http://forum.ubuntu-it.org/index.php...h=117380;image]("http://forum.ubuntu-it.org/index.php?action=dlattach;topic=484222.0;attach=117380;image")

more info:
gio@GIO-PC:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe3220000 irq 48

gio@GIO-PC:~$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: Intel [HDA Intel], dispositivo 1: STAC92xx Digital [STAC92xx Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

what could i do?
i hope to fix this problem
thx

---

### Post by giogiomogio on 2011-10-13
up

---


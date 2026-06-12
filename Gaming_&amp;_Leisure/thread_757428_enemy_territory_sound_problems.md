---
title: "enemy territory sound problems"
date: 2008-04-16
forum: Gaming &amp; Leisure
---

### Post by luposolo on 2008-04-16
i just installed enemy territory it works perfectly fine the only problem is im not getting any sound

---

### Post by luposolo on 2008-04-17
this is the message it is giving me 

------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp

---

### Post by citaworvk on 2008-04-22
I have the same problem. Sound work in all the other applications. I also have USB speakers and no literal sound card.

---

### Post by NR1224 on 2008-04-22
do the following, in this order;

sudo killall esd
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
et

works for me:guitar:

---

### Post by hero1900 on 2009-05-30
thank you for help

---


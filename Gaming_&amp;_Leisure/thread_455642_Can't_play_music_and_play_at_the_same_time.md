---
title: "Can't play music and play at the same time?"
date: 2007-05-26
forum: Gaming &amp; Leisure
---

### Post by GvsE on 2007-05-26
Hi!

Im unable to play music with amarok or any other players while i play wow with wine. I have tried to search for help to get this work. If i play wow, quit or after this new patch cant quit so i need to reboot so i can listen music or watch videos etc. 

Wine sound settings:
[http://img511.imageshack.us/img511/2950/kuvakaappaussa0.png](http://img511.imageshack.us/img511/2950/kuvakaappaussa0.png)

---

### Post by MrMatt2532 on 2007-05-26
You will need to use alsa-oss. Check here [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) in the voice chat section.

---

### Post by GvsE on 2007-05-27
Hmm, that didn't help when i changed from winecfg to alsa. Still cant hear voices in game but music plays fine.

---

### Post by GvsE on 2007-05-28
Anyone got solution for this?

---

### Post by Ventrue on 2007-05-28
Install: alsaplayer-jack, jackd, libbio2jack0, libbio2jack0-dev, libjack0.100.0-0, libjack0.100.0-0-dev, libjackasyn0.
Then change OSS to ALSA in winecfg.

---

### Post by lakersforce on 2007-05-28
use alsa-oss (aoss)

---

### Post by d4bn3y on 2007-05-31
Wow these solutions sound great, anyone wanna give some step-by-step instruction on doing these?

---

### Post by kcmanc87 on 2008-07-22
Yeah I've got the same problem. I'm using cedega though, but when ever I use sound in wine I can't use sound in anything else.

---


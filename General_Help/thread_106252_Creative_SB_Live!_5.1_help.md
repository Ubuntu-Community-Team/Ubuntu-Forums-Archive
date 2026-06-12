---
title: "Creative SB Live! 5.1 help"
date: 2005-12-20
forum: General Help
---

### Post by RaisedFist on 2005-12-20
Hi... I have a Creative SB Live 5.1 soundcard and just bought a set of creative 5.1 speakers and I cannot set the soundcard up to use all the speakers. Now it only works with the subwoofer and the front speakers. Rear and center speakers are mute.
How can I do this??

Thanks in advance!

---

### Post by schdefan on 2005-12-20
post the output of lsmod|grep snd. You have to be sure that the module (with is the driver in other words) of your soundcard is loaded.
when you open alsamixer check the volume faders of all the channels maybe they are muted by default nad also look at the description if it says Creative SB Live

schdefan

---

### Post by RaisedFist on 2005-12-23
I finaly made it work.. from alsamixer I set rear jack to get front output... it works!!!

---


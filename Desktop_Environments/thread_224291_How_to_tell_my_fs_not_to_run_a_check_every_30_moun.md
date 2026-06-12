---
title: "How to tell my fs not to run a check every 30 mounts"
date: 2006-07-27
forum: Desktop Environments
---

### Post by AppleNick on 2006-07-27
What would I do to tell my filesystem not to run periodic checks?

---

### Post by reacocard on 2006-07-27
```
gksudo gedit /etc/fstab
```
change the number at the end of each entry to zero. voila, no more fsck.

---

### Post by Anduu on 2006-07-28
> **AppleNick said:**
> What would I do to tell my filesystem not to run periodic checks?

Not the best idea...it is set up that way for a reason.

---

### Post by MWAAAHAAA on 2006-07-28
What fs are you using? With large partitions and an ext2 filesystems, those fcks really suck, because it takes so long. You might want to consider changeing to ext3 or reiserfs anyway.

What the guy above said is true, do NOT turn it off completely.

---

### Post by kabus on 2006-07-28
Don't turn it off completely, just use the tune2fs command to up the maximum number of mounts between checks. Use slightly different numbers for different partitions so checks get spread out a bit.

---

### Post by Anduu on 2006-07-28
Not to mention if the disk checks are becoming annoying you are rebooting waaaaaay to often....Linux is not Windows....you don't need to reboot 5 times a day to stay stable ;)

---

### Post by der_joachim on 2006-07-29
> **Anduu said:**
> Not to mention if the disk checks are becoming annoying you are rebooting waaaaaay to often....Linux is not Windows....you don't need to reboot 5 times a day to stay stable ;)

I only leave my PC on when I'm actually using it (energy prices are very high up here). 

Anyhoo, the command the OP is looking for, is ```
tune2fs -cXX /dev/hdXY
``` The Xs and Ys are of course the numbers and letters of the desired partitions and settings. ;)

---


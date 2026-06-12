---
title: "Ubuntu gone after installing windows xp"
date: 2009-01-28
forum: Desktop Environments
---

### Post by deep_blue on 2009-01-28
Earlier, I had Windows XP SP3 installed in C: drive and Ubuntu in F: drive. I was getting a option menu to select either Windows XP or Ubuntu when computer start.

But after I fromatted C: drive and again installed Windows XP SP3 it is not showing a selection menu; rather windows xp gets started automatically.

Is there a way I can get the earlier selection menu while computer starts?

---

### Post by Mason Whitaker on 2009-01-28
F12 or the Tab button for most computers once you see the distributors logo on bootup.

---

### Post by ChimpofDOOM on 2009-01-28
Whats happened here is that... when you reinstalled XP, it wrote over the Master Boot Recrod (MBR) and automatically set XP as the default operating system.

You could use a SuperGRUB disc to restore the GRUB menu to allow you to boot back into Ubuntu

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Good luck :D

---

### Post by Lee_Machine on 2009-01-28
When windows is installed it erases the hard drives boot sector and puts its Master Boot Record there (MBR)

You need to put in a live CD of ubuntu and reload GRUB.

See [THIS]("http://http://ubuntuforums.org/showthread.php?t=576788") post for instuctions.

---


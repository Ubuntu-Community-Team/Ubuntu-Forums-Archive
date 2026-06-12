---
title: "OS trouble"
date: 2009-03-20
forum: General Help
---

### Post by realizee on 2009-03-20
Hi, I recently installed ubuntu on my computer and I did later install XP on it. What i've noticed was that it didn't came up a boot menu to choose whether I like to boot Ubuntu or XP. So i reinstalled Ubuntu but now I can't come into XP. It just works i safemode.

Please help!

---

### Post by Felix_the_Mac on 2009-03-20
Do you know how many partitions you have on your hard disk?
Install and run gparted to find out.

You need to add Windows to /boot/grub/menu.lst
My XP entry looks like this:

> title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

N.B. on my PC XP is on the 1st hard disk in the 2nd partition.
Counting starts at zero therefore: (hd0,1)

Good Luck!

---


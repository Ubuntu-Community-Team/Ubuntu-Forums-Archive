---
title: "Erasing the windows XP partition?"
date: 2009-04-14
forum: General Help
---

### Post by mcfields on 2009-04-14
Ok, so I have windows XP on this old, CD-DRIVELESS laptop and it was slow so i installed ubuntu through wubi. The hard drive is now partitioned with XP in one and Ubuntu in the other. I just want to use ubuntu, don't need XP or want any of the files on this computer, just ubuntu. How can i go about totally wiping the XP partition (including XP) and giving all that space to the ubuntu partition? Sorry if this is worded strangely. I don't talk about this kind of stuff much.

---

### Post by prem1er on 2009-04-14
There are many posts on this topic. Do some searching on these forums and google.  Gparted is the partition editor included in ubuntu so search around for that.

---

### Post by mcfields on 2009-04-14
But the ones im finding have CD Drives. Theres so many variations lo.

---

### Post by prem1er on 2009-04-14
> **mcfields said:**
> But the ones im finding have CD Drives. Theres so many variations lo.

CD drives make no difference in creating, or in your case, removing a partition.  If you have ubuntu already running on your computer than you have gparted already installed and you can use that tool to remove your windows partition and resize your linux partition.

---

### Post by JC Cheloven on 2009-04-14
> **prem1er said:**
> CD drives make no difference in creating, or in your case, removing a partition.  If you have ubuntu already running on your computer than you have gparted already installed and you can use that tool to remove your windows partition and resize your linux partition.

Please, note that the O.P. (as far as I understand) has ubuntu inside xp via wubi, so in the same partition although he claims they are in separate partitions. He can't remove partitions currently in use.

I suppose that this pc isn't able to boot from usb either (this would solve the problem, reinstalling from usb).

I think your best chance is a fresh conventional install of ubuntu. The problem is ¿from what media?. If you can't boot from cd or usb ... well, only a network boot remain. My advice would be to get a cd drive, they're cheap nowadays.

---


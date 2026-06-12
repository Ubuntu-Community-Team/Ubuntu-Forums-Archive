---
title: "QTParted issue"
date: 2006-08-13
forum: Desktop Environments
---

### Post by John Jones on 2006-08-13
Hi to all.

I'm not sure which category this query belongs in, (still pretty much a newbie).

I tried running QTParted, just to have a look at it, and I got the following in the terminal window; -

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.

I've no idea what this means, and when I tried to run e2fsck, it wouldn't play.

Has anybody got any thoughts?

Cheers,

John :???:

---

### Post by jordilin on 2006-08-13
Have you tried gparted? Try it and see if happens the same. Partitions must be unmounted, if I'm not wrong.

---

### Post by John Jones on 2006-08-13
No, I hadn't, but I've installed it now, and it seems to work okay.

So I'll forget about QTParted for now, unless someone can tell me what's going wrong.

Thanks for the tip.

John :)

---

### Post by jordilin on 2006-08-13
> **John Jones said:**
> No, I hadn't, but I've installed it now, and it seems to work okay.

So I'll forget about QTParted for now, unless someone can tell me what's going wrong.

Thanks for the tip.

John :)

Qtparted and gparted are more or less the same, the main difference is that one is developed by using Qt and the other GTK, so if Gparted works fine, I would forget qtparted :)

---

### Post by John Jones on 2006-08-13
Okay, I'll forget about QTParted.

It wasn't that I needed to use a partitioner anyway, I was just exploring.

Thanks again.

John :-D

---

### Post by bruce89 on 2006-08-13
You can't modify mounted partitions anyway, the only way you can modify your partitions is with a LiveCD, such as the [gParted one]("http://gparted.sourceforge.net/livecd.php").

---


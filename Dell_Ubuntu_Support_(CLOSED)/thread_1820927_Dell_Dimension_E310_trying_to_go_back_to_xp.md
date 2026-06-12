---
title: "Dell Dimension E310 trying to go back to xp"
date: 2011-08-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Vincent0225 on 2011-08-08
I have two desktops currently operating with Ubuntu 11.04 and i was wondering can anyone give me advice on how to revert my dell dimension e310 back to Windows XP? Ubuntu deleted all the partitions of Windows Xp and whenever i try to install using a CD it says there are no drives and then a Blue screen of death pops up saying there is an error with setupdd.sys. Please help me. Any advice would be helpful.

---

### Post by Basher101 on 2011-08-08
Try to boot from a live cd into ubuntu and reformat your WHOLE hdd to NTFS (you want only xp on it yes?). Then retry installing xp

---

### Post by Vincent0225 on 2011-08-08
> **Basher101 said:**
> Try to boot from a live cd into ubuntu and reformat your WHOLE hdd to NTFS (you want only xp on it yes?). Then retry installing xp

Thank you. i will try doing this right now.

---

### Post by Vincent0225 on 2011-08-08
Well i tried to boot the windows xp cd while on my desktop of ubuntu and it would only see the files inside the cd but it wouldnt let me boot up the cd.

---

### Post by trae329 on 2011-08-09
> **Vincent0225 said:**
> Well i tried to boot the windows xp cd while on my desktop of ubuntu and it would only see the files inside the cd but it wouldnt let me boot up the cd.

Don't boot the CD from Ubuntu. Reboot your comp, and boot from the XP CD. From there you can install XP, not from Ubuntu.

If you still have problems, use GParted on the Ubuntu Live CD to reformat your whole partition to NTFS or FAT32 (whichever you prefer, FAT32 can only store 4GB max / file.).

---


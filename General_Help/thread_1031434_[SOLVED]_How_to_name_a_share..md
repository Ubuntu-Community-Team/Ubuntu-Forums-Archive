---
title: "[SOLVED] How to name a share."
date: 2009-01-05
forum: General Help
---

### Post by zacktu on 2009-01-05
On my dual-boot system I mount my MS Windows data partition with an entry in /etc/fstab.  It is mounted as /mnt/windows, but the icon on the desktop is "21.2 GB Media." 

On the other hand, I mount hosts on my network with the mount command.  In those cases if the mount point is /mnt/remotehost, then the icon on the desktop is "remotehost". 

Is there an argument for fstab that enables me to label the windows mount?

---

### Post by zob on 2009-01-05
If you don't mind that every internal drive gets mounted automatically, you should let HAL mount it.
Problem is that only external drives are mount by default by ubuntu, not the internal ones. But there is an easy "fix" to that if you [read this.]("http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html")
At least my drives, this way, shows op with the names I gave them when I first created the partitions. You could also try to rename your partitions with gparted, if that is the problem.

---

### Post by kanikilu on 2009-01-05
> **zob said:**
> You could also try to rename your partitions with gparted, if that is the problem.

That's what I was going to suggest, since drives that I've specifically set a volume name on show up with that name, while drives that don't have one set display something similar to what he was saying (e.g. "## GB Media").

---


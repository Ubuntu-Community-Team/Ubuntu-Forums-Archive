---
title: "Gparted"
date: 2008-12-21
forum: General Help
---

### Post by antoinedl on 2008-12-21
Hi everyone,

I used to run Gparted for every partition change I had to do... But since a few weeks, one of my partiton (the one where Vista is installed), I cannot resize or move the partition... Even if I try Gparted from the live CD (where no partition is supposed to be mounted) and if I defragged my partiion where Vista if installed (with many defragmentation apps), I cannot access partition managing option from Ubuntu (resize or move)...

Can someone tell me what would be the little magic app or library to install to fix this ?


Thanks !

Antoinedl

---

### Post by sockrebel on 2008-12-21
did you try "chkdsk -f" in the Windows partition?

---

### Post by drs305 on 2008-12-21
I know in the older versions of gparted there were limitations on what it could do with NTFS partitions. I believe that installing 'ntfsprogs' enabled gparted to run some of those tasks. The newer versions on the liveCD and the gparted cd have that capability - I don't know if the gparted package in the repositories can or not. If you don't have a recent version of gparted try to get it or try installing ntfsprogs.

---

### Post by caljohnsmith on 2008-12-21
Vista has its own Disk Management tools--have you tried using Vista to shrink its own partition? You can access Disk Management by right-clicking My Computer and selecting "Manage" or something similar to that. I would recommend trying that first if you can.

---


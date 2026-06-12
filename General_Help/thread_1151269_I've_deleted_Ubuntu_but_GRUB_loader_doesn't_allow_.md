---
title: "I've deleted Ubuntu but GRUB loader doesn't allow me to boot my PC"
date: 2009-05-06
forum: General Help
---

### Post by danyboy8a on 2009-05-06
hello there.... Here's my problem: 

At first I had my HP pavilion laptop with Windows XP Home, Windows Server 2003 and Ubuntu 8.04 installed. But now I've installed Ubuntu in my new Dell Laptop, so I tried to delete the partitions containing Ubuntu. These were three partitions: 

One reiserfs for /
One linux-swap
One FAT32 for shared files between the three OS

I used a partition manager to rearrange the partitions so now I could just have 2 primary for each windows. But when the partition manager finished and restarted my computer, appears the original GRUB loader saying:

GRUB loading stage1.5.

GRUB loading, please wait...
Error 22

So now I cannot load either Windows and I don't want to format the whole HD to fix this (still...) 

I just need to remove that GRUB from the BIOS or wherever it is (somehow...) I've tried to modify the boot.ini but that's not the solution.

Please help!!!

Dan

---

### Post by taurus on 2009-05-06
You need to remove GRUB from MBR.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by salvachn on 2009-05-07
You could try using the XP Restore CD, or Vista install CD to reinstate your MBR.

---


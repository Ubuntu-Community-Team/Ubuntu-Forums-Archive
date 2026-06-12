---
title: "GRUB - Cannot boot to CD"
date: 2008-12-04
forum: General Help
---

### Post by gothdaddee on 2008-12-04
Good day everyone.  I'm having problems booting to CD.  Ever since I used GRUB to dual boot between Gutsy Gibbon and WinXP I cannot get my winxp cd installer to boot.  The CD drive is already set as the first boot priority in BIOS and I can boot using any linux LiveCD so that means the BIOS or my hardware is cleared from this error.  I tried booting my WinXP CD in several other machines (ubuntu without any other OS and WinXP without any other OS and dual boot machines) and it works perfectly so my CD is also cleared.  At first I just ignored it thinking that I won't need it anyway.  But now I have to repair the WinXP installation but I cannot do so because I cannot boot from the WinXP CD.  I don't know where else to look.  I've tried searching to no avail.  Please help!  Thanks in advance!

---

### Post by caljohnsmith on 2008-12-04
So what exactly happens when you try and boot the Windows CD? Does it give any errors? One thing I would recommend checking is your HDD's partition table, because if that is even slightly corrupt, that often causes the Windows Install CD to choke. How about in Ubuntu, open a terminal (Applications > Accessories > Terminal), and please post the output of:
```
sudo fdisk -l
```
Next make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---


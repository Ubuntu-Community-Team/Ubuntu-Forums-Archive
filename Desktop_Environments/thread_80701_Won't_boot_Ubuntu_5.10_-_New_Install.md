---
title: "Won't boot Ubuntu 5.10 - New Install"
date: 2005-10-22
forum: Desktop Environments
---

### Post by DavittJPotter on 2005-10-22
OK, I've searched around, but can't find my answer, so I'll try it here... :)

Ubuntu appears to install perfectly, and near the end of the install process, detects Windows XP Professional as another OS (which is correct), and asks me to install Grub to the MBR.  I tell it OK, reboot, but it never goes to a grub screen - just straight to Windows.  Hmmm.

Any ideas?  I've even tried reinstalling, no luck.

Drives:

hda1 is 80GB for WinXP, hda2 is 160GB, 20GB at beginning for expansion, 100GB for WinXP storage, 20GB for Ubuntu at the end.

Help!  ;) 

Thanks!

---

### Post by Ampersand on 2005-10-22
Try going into the bios (press f1 or whatever you're told to press to enter setup when you start booting), then change the boot order so your other hard drive boots first. If you have the manuals for your computer, they should tell you how to do this, it varies depending on the motherboard.

---


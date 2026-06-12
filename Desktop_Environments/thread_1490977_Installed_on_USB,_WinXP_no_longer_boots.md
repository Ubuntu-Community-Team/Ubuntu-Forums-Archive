---
title: "Installed on USB, WinXP no longer boots"
date: 2010-05-23
forum: Desktop Environments
---

### Post by markeb on 2010-05-23
Hello - I am new to ubuntu and am stuck, hoping someone can help me.
 
I installed Ubuntu 10.04 on a USB hard drive after booting the desktop installer ISO on a USB flash stick. My laptop already had Windows XP installed on the internal hard drive and i did not load Ubuntu onto that disk.
 
I can no longer boot the Windows OS. My laptop shows a grub rescue prompt with "no such device" error. I can mount the internal hard disk ("system drive") and see all the Windows files from within the Ubuntu desktop installer.
 
Is there a way to restore my Windows system drive to boot or do I need to reinstall? 
 
Thanks in advance for your help. This really has me in a bind.
 
Mark

---

### Post by MooPi on 2010-05-23
When you installed Ubuntu,  Grub found Windows and now your boot order is screwed up because the grub info is on the flash drive. Insert you flash drive then when grub starts scroll down to Windows and see if it loads then. Most likely you will need to boot to a Windows install disk to correct your master boot record. After you boot from the CD choose Recovery console or ( r ). Open a command prompt and ```
fixmbr
```This web page explains the steps.
[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)

---

### Post by markeb on 2010-05-23
I tried winxp recovery and setup CDs, but they blue screened. I don't think they can see the HDD anymore. I say this because I also tried a Vista recovery CD and it failed to detect a HDD (but didn't crash).
 
When I boot from the ubuntu setup USB I can see the internal HDD, but I must manually mount it first. When I originally setup Ubuntu on the external USB HDD the internal HDD automatically appeared without first manually mounting it.
 
So I wonder if the ubuntu installer did something to the disk so it is not active by default???
 
Any insights much appreciated.
 
Thanks,
Mark

---

### Post by markeb on 2010-05-23
Problem solved...Lilo did the trick in fixing my Windows XP MBR!
 
[http://ubuntuforums.org/showthread.php?p=9349106#post9349106](http://ubuntuforums.org/showthread.php?p=9349106#post9349106)

---


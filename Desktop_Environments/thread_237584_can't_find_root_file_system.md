---
title: "can't find root file system"
date: 2006-08-16
forum: Desktop Environments
---

### Post by beppe! on 2006-08-16
hi!

my system is:
ASUS P5LD2, 1024 MB RAM, nVidia 6600, Pentium D830 (3.0GHz), 160 GB stripe HD (2x80 MB) with WinXP installed and maxtor HD 40 GB (secondary hard disk).

Now my problem is:
I've tried to install ubuntu on the 2nd hard disk (not on the raid volume), all is gone ok... when I reboot and i try to run ubuntu on the first screen I could see: 
"Loading essential driver: ok"    
"Mounting root file system"      
"waiting for root file system"   
and then the system stops.

after a while (few minutes) the screen change and i read:
ALERT! /dev/hde3 does not exist - dropping to a shell

What happen? May I made a mistake? What should I do?

thanks very much (and sorry for my bad english!!!!)

see you!

---

### Post by Lunar_Lamp on 2006-08-16
Well, I don't know your partitioning details, but looking for the root file system on hde3 seems strange.  This could be a result of the RAID though, which I have no experience with.  You may want to check that you have set grub up correctly to be looking in the correct place.

---

### Post by foopirata on 2006-08-16
Your disk controller is recognized by the install program, but not by the actual kernel installed on your hard disk. I am having the same problem using a PERC/5 card - the install goes fine, but the kernel put into the disk doesn't have the appropriate modules.
You can fix this by booting the live system again and mounting your installed partition, copying the kernel from the live system into the partition (don't forget /lib/modules/`uname -r` as well) and modifying your grub.conf. Then from there on, make sure any kernel you install has the modules for your RAID card (which is probably the controller of your second disk).
I hope this helps any.

---


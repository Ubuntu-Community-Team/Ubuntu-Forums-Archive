---
title: "Getting Rid of Ubuntu Bootloader Thingy"
date: 2009-05-29
forum: General Help
---

### Post by The_Lost_World on 2009-05-29
So I tried to uninstall the Ubuntu bootloader that I installed when I selected the "help me boot from cd" option on the live CD, but I get an error. So I thought I'd just do it the old fashioned way and delete the file "ubuntu" in my C:\Windows folder. I'm not so sure though; will anything bad happen?

---

### Post by munky99999 on 2009-05-29
You want to delete grub?

I would suggest [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Boot loaders typically live in the masterbootrecord not c:/windows.

---

### Post by cariboo on 2009-05-29
It sounds like you did a wubi install. That shouldn't make any difference though. If you have a Windows install disk, just boot from it and go into the recover console and run FIXBOOT and FIXMBR.

To uninstall Ubuntu, go to Start-->Control Panel-->Add/Remove Programs and uninstall it.

---

### Post by JCoster on 2009-05-29
..or alternatively, if trying to return to a Windows install and you're running Vista, just click the startup repair button when you enter the Vista install CD.

If i'm correct, this should rewrite the bootloader to the Vista default.

---

### Post by The_Lost_World on 2009-05-29
> It sounds like you did a wubi install. That shouldn't make any difference though. If you have a Windows install disk, just boot from it and go into the recover console and run FIXBOOT and FIXMBR.
Yea, I'm pretty sure it's Wubi. I don't have a disk, it didn't come with one.

> To uninstall Ubuntu, go to Start-->Control Panel-->Add/Remove Programs and uninstall it. 
Yea, but I get some sort of error. Says it can't find some file. So I figured I'd just delete what you say is the Wubi install (In C: there's a file called "ubuntu") manually. I'm just asking if that will cause any problems or not.

You see, I've got Windows Vista and openSUSE in a dual-boot configuration and when GRUB loads when I power up my system, it gives a "Windows" option, but when I select that I have to select "Windows" or "Ubuntu" again.

---

### Post by The_Lost_World on 2009-05-30
bump

---


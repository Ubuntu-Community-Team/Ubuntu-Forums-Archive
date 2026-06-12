---
title: "Reinstall Grub without a CD"
date: 2009-05-03
forum: General Help
---

### Post by jon.mithe on 2009-05-03
I had to reinstalled windows, and in its normal fashion its nuked my mbr, grr.

Normally I would boot up on a live CD and fix it from there, however, my live CD is knackered and I do not have a blank CD to burn a new one :/  

Does anyone know of a way to install grub from windows?

I tried a USB live disk, but I cant get my bios to use it to boot for some reason. I tried also mounting the live CD iso and installing ubuntu into a directory on my windows partition.  This fails to boot on resart, I think it was looking for the CD.  It installed some windows boot manager. 

I'm stuck :confused:

Thanks for any help - Jon

---

### Post by Archimedes0212 on 2009-05-03
[http://ubuntuforums.org/archive/index.php/t-190820.html](http://ubuntuforums.org/archive/index.php/t-190820.html)

Previous post that had your same problem.  'missingxtension' mentions the use of w32grub.zip.  Hopefully that works.

Best of luck.

---

### Post by jon.mithe on 2009-06-07
Thanks.

Unfortunately that did not work, nor some other random things I tried (some boot app that loads with the windows boot loader and trys to educate throughout the utility). Tried a live CD but failed, think my DVD RW is not a happy bunny.

Anywhos, solved it buy trying again to install ubuntu into a folder from windows (via a virtual drive / iso), this time on restarting it was in the windows bootloader, got into a console and fixed in 10 seconds.

<3 linux :P

For anyone stuck / reading this I ran the following commands:

```
sudo grub
root (hd0,9)
setup (hd0)
```

where hd0 is the hard drive number (I think it goes hd0, hd1 etc) and the 9 is the partition I installed ubuntu on with the grub configuration information menu.lst or somethings.

---

### Post by MasterNetra on 2009-06-07
Could order a CD? Or..request a free CD, granted the latter would take weeks to reach ya.

---

### Post by lindsay7 on 2009-06-07
If you have usb, you can get Ubuntu to put on it from Unetbootin. See the web site. Then enter the commands below.


I think these are the correct commands

sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hdx)
quit

---

### Post by VMC on 2009-06-07
Do you have a floppy disk? SGD has a floppy image.

---


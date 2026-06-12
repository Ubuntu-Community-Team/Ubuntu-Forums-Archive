---
title: "Error 22 Help!"
date: 2009-05-10
forum: General Help
---

### Post by Darksun45230 on 2009-05-10
I recently installed Ubuntu. Well, I didn't like it as much as I my XP (which I don't have the CD for -_-) so I uninstalled it except everytime I boot up it comes with an Error 22 message. I read on the forums that I need the Windows Boot cd in order to repair this but I don't have it any longer. And regrettably I reinstalled Ubuntu with minmal memory as to go back to windows. I attempted to delete the partitions again (I did something wrong) and now I'm on the wrong side of both OS's. I keep getting Error 22, and the only operating system I can use is on the Ubuntu CD.

Tell me how to fix it! I'm running out of options, and also I can't let anything happen to my XP. I have important files (work) that can't be moved. If anyone were to help me, I would be eternally grateful.  :(

Edit: Upon further looking I found this topic.

[http://ubuntuforums.org/showthread.php?t=622828&highlight=error+22](http://ubuntuforums.org/showthread.php?t=622828&highlight=error+22)

I attempted to follow the process above but everytime I enter "**sudo apt-get install ms-sys**" on the console I get "Sudo: unable to execute /usr/bin/apt-get: Input/Output Error."

---

### Post by zvacet on 2009-05-10
Try with [Super grub.]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by Darksun45230 on 2009-05-10
> **zvacet said:**
> Try with [Super grub.]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

How exactly? I have a laptop and only one CD drive which Ubuntu uses. I have a PSP as a possible alternative to USB. I just don't know how to make it work (already tried placing Boot in Root directory and nothing happened.)

Update: I attempted to follow the instructions in this link.

[http://www.supergrubdisk.org/wiki/SGD_Howto_make?phpMyAdmin=4d5aa646470e3977a158303759c2efde#How_to_make_a_Super_Grub_Disk_USB](http://www.supergrubdisk.org/wiki/SGD_Howto_make?phpMyAdmin=4d5aa646470e3977a158303759c2efde#How_to_make_a_Super_Grub_Disk_USB).

Specifically these sections.

> 
/dev/sdb1 on /media/all type ext3 (rw,nosuid,nodev,uhelper=hal,data=ordered)
Now we have learnt that the USB device is called: /dev/sdb1 [B](From now on... you should continue the howto with your own USB device which might be /dev/sda1 or something similar).
[/B] 

Does it mean I have to input the entire line in the following instructions...?

> 
Now we will use the /dev/sdb (/dev/sdb is ther hard disk where /dev/sdb1 partition is located) device in grub to associate a virtual grub device (hd3) to it and work with it. 
 grub
**grub>**device (hd3) /dev/sdb
**grub>**root (hd3,0)
**grub>**setup (hd3)
First, did the /dev/sdb mean the entire line? Second, I *still* can't get it to be recognized when booting. What could be the problem? Please I've been working on this problem for hours!

---

### Post by zvacet on 2009-05-12
I hope [this]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk") will make more clear what to do and why.It is just install of SGD on flash drive.Read [here]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk") how to use it.Sorry for late response.

---


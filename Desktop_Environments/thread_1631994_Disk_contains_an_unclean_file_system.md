---
title: "Disk contains an unclean file system"
date: 2010-11-27
forum: Desktop Environments
---

### Post by harshadgada on 2010-11-27
I had XP and Ubuntu 10.4 LTS installed in different partitions.  Now I couldn't access XP and then Ubuntu.  So I tried re-installing XP.  Didn't work.  Installation just doesnt complete.  I then tried re-installing Ubuntu in a different partition. Same doesn't work. When trying to boot via the live CD the following error message comes:"Disk contains an unclean file system".  I cant boot via the Live CD also.

The question that I have is 
a) whether the HDD and all the data in it has gone for good? 
b) Does the error message means that the Hard Disk is detected but cannot be mounted?
c) Is there any chance that I can connect my hard disk in another machine as a second hard disk and boot via a live CD and access the data in it?

The disc had 4 partition with XP in one; 2 partition full of data and Ubuntu in the 4th partition.

Being my first post and thread, I don't know whether this is the correct forum?

---

### Post by pietjanjaap on 2010-11-27
Check your bios for virusprotection of the mbr, disable this, maybe this is why you can not install linux or windows.

Unclean system means the harddisk is disconnected wrong wenn using, like system reset, or pulling usb harddisk of the pc without releasing it in the software first.
Or the harddisk is broken, normally not.

Booting from cd is not working, has nothing to do with a bad harddisk.
Change de boot settings in de bios, remove everything, and put de cd only in it.

If you can boot from the livecd, then start gparted, go to all the linux parttitions, and with the mouse wright click on every parttition, and chosse check, this is fsck from linux, then reboot linux.

For windows you need to run chkdsk, from the windows cd, boot , choose "R" to get to the "recovery console", similar to dos, do chkdsk for all windows parttitions. Then reboot.

---

### Post by Aryamaan on 2010-11-28
Go to the BIOS and change boot settings. Set your primary boot device to your CD-ROM. All you actually have to do is open up your CPU and plug in your hard disk properly. If you're unsure of whether you can do that, I would suggest calling a technician.

---

### Post by Aryamaan on 2010-11-28
To go into BIOS press delete at boot screen. Or whatever button is specified in the bottom of your screen where it says "Press <button> key to enter setup".

---

### Post by harshadgada on 2010-11-29
> **pietjanjaap said:**
> Check your bios for virusprotection of the mbr, disable this, maybe this is why you can not install linux or windows.

Unclean system means the harddisk is disconnected wrong wenn using, like system reset, or pulling usb harddisk of the pc without releasing it in the software first.
Or the harddisk is broken, normally not.

Booting from cd is not working, has nothing to do with a bad harddisk.
Change de boot settings in de bios, remove everything, and put de cd only in it.

If you can boot from the livecd, then start gparted, go to all the linux parttitions, and with the mouse wright click on every parttition, and chosse check, this is fsck from linux, then reboot linux.

For windows you need to run chkdsk, from the windows cd, boot , choose "R" to get to the "recovery console", similar to dos, do chkdsk for all windows parttitions. Then reboot.

How do I disable the virusprotection of the mbr?????  I couldn't find the option anywhere in bios. 

Trouble is, when I put the windows cd, it doesn't detect my hard disk.  And so I cant run the chkdsk utility.  

Let me try the Linux thing again after removing the every thing from the bios.

Thnx for the help anyways

---


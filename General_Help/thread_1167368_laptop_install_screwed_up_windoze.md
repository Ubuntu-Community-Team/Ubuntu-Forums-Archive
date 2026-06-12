---
title: "laptop install screwed up windoze"
date: 2009-05-22
forum: General Help
---

### Post by georgec32 on 2009-05-22
Hi all.

I'm a ubuntu newbie (total linux amateur).  I tried to install ubuntu 8.10 on a USB HD attached to my laptop (Compaq 6910p running XP Pro).  I used the manual partition option on the live CD, following instructions from some websites showing how to do that.  I re-sized the 250 Gb NTFS partition to 150 Gb, then made a 30Gb ext3 partition mounted at '/', a 5Gb swap partition, and a 65Gb FAT32 partition mounted at '/home'.  It seemed to install OK, then said to reboot my computer.  I did a re-boot and the ubuntu didn't load (gave me a 'media test failure, check cable' error).  I removed the USB HD and rebooted again, intending to drop back to square one w/ windows, but now I can't boot to windows.  I get an error saying: "GRUB loading stage 1.5
GRUB loading, please wait
Error 21" 

It just stalls at that point.  Fearing I'd screwed up my windoze partition, I rebooted from the Ubuntu live-CD and opened partition manager, and that shows my windoze partition still there, with the boot flag still set .. 

Can anyone tell me how to get rid of the GRUB error?  I can't get into DOS or anything on my laptop, so I don't -think- I can access my boot.ini file or any of that stuff ... 

thanks in advance for helping a newbie recover from his idiot screwup :)

george

---

### Post by raymondh on 2009-05-22
Hello Georgec32,


I have seen posters recommending also the use of supergrub which can also fix grub to work on both XP and Ubuntu.  Try this out first.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

To try to recover your XP bootloader  (this will overwrite your GRUB and you will have to re-install grub to access your ubuntu install)

1. Boot up with your Windows XP disc.

2. Select the option Recovery Console.

3. At the prompt, type "fdisk /mbr" (without the quotes of course)

4. Restart your computer.

Good luck and regards,

---

### Post by raymondh on 2009-05-22
also, Herman's got great documentation about supergrub

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk)

Regards,

---

### Post by georgec32 on 2009-05-22
> **raymondhenson said:**
> also, Herman's got great documentation about supergrub

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk)

Regards,

wow that was quick!  Many thanks to both of you :)  I downloaded supergrubdisk, booted w/ that, pointed to the windows option, and problem fixed.  Whew!  Thanks!  

george
aka relieved :)

---

### Post by raymondh on 2009-05-22
> **georgec32 said:**
> Many thanks to both of you :) )

Glad to be of service (from the both of us) :)

Keep that supergrubdisk and herman's documentation handy/bookmarked for future reference.

Happy Ubuntu-ing.

PS.  Would you like to mark the thread solved?  Go to your first post > edit > advanced > type SOLVED in front of the original title > save.

Again, regards

---


---
title: "Dual Boot Problem"
date: 2007-07-02
forum: Dell  Ubuntu Support
---

### Post by cosborn72 on 2007-07-02
Hi guys,  I have having an issue setting up dual-boot for my new ubuntu dell machine.  (I know, I shouldn't use windows....it is a necessity, believe me.)

Knowing that it is best to install XP first, I tried to run the XP system disk.  It loads the drivers, then says "Windows starting up)....then... the Blue Screen of Death.
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
A problem as been detected and windows has been shut down to prevent damage to your computer.
Check for viruses on your computer.  Remove any newly installed hard drives or hard drive controllers.  Check you hard drive to make sure it is properly configure and terrminated Run ChKDSK /F to check for Hard drive corruption, and restart your computer. 

Technical Information:
STOP 0x0000007b (xF78Ee2524,. etc.....

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>


I don't know if this is because there is no MBR.  My understanding is that the XP install disk should fix that.  Do I need some third-party controller for the 250 SATA data-burst drive?  

One other note, I have tried this with a XP pro CD, a copy of the XP pro CD and an XP Home CD.  I get the same result.

---

### Post by logos34 on 2007-07-02
A new Dell Ubuntu computer!  Great choice!.  

Check the BIOS--make sure it's recognizing the sata drive.  (Set it to 'auto' detect).  If you have a floppy drive flash the BIOS with new update, if any (that's the first thing I check).

There's nothing on the drive or mbr (no bootloader there yet because no OS), but that's not the problem.  If and when you manage to install winxp, it will put it's own bootloader on the mbr, which will be overwritten by Grub as soon as you install Ubuntu.

---

### Post by cosborn72 on 2007-07-02
Thanks,  I was able to fix it.  I tried a few things, but I think that work worked was going into the BIOS and disabling the RAID configuration.

Who knew?

---

### Post by logos34 on 2007-07-02
why in the world would they ship these things with raid enabled?

---

### Post by d2m3y77 on 2007-09-26
Recently the power supply of my PC was spoilt and I moved my harddisk to another computer. As I didn't separate the root and home directories  in the previous ubuntu installation and I did not want to overwrite my data, I re-install ubuntu on a partition /dev/hdb4 of the second harddisk.

I set the previous ubuntu partition /dev/hda5 on the first harddisk as /home during this re-installation. After booting up, I moved the contents of the previous home directory (now /dev/hda5/home/home/user) to /home ( that is, /dev/hda5/home) and then deleted or other "unnecessary" system files and folders on that partition (since the installation created another set of running system folders and files on the second partition of the second harddisk).

When I boot up again, I find that I can bootup the new ubuntu, another previous windows XP Home (a non english version), but I couldn't boot into my english windows XP Professional. (I can select this option, but I get an error message shortly after.)

After selecting the english windows version, I get the blue screen telling me that "...windows has been shut down to prevent damage to your computer..."

My guess is that by deleting all the system folders and files on the old ubuntu partition (which is now the new ubuntu /home), the computer could not find some required file/files to boot into the english windows residing on dev/hda5.
As I don not wish to spend another several hours reinstalling windows and ubuntu and many others applications that I need, and I need that windows for
some purposes, is there any way to savage the windows?

---


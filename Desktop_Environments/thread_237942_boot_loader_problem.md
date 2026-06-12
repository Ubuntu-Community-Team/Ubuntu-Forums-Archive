---
title: "boot loader problem"
date: 2006-08-16
forum: Desktop Environments
---

### Post by tbobo05 on 2006-08-16
I just installed Ubuntu 6.06 on my PC with the live cd.  My computer has a default SATA harddreve and a newly installed IDE harddrive.  I installed Ubuntu to the IDE drive (hdb) but cannot boot into it now (i think it installed GRUB to that location instead of the SATA drive, SDA).  How can I install the boot loader to the SATA drive?

---

### Post by silvagroup on 2006-08-17
just recentky had the exact problems. It appears that for soem reason when installing to stat drive Dapper writes to your primary drive wiping it out. I've spent the last week trying to see if I can recover it somehow. Have found a few things such as testdisk and dd_rescue that I experimented with but have bnot committed to any changes for my primary drive because I want to make sure I can recover it and not have ot totally blasted into the black hole of the cyber neverlands. s always good case for backups (stupid me) and also good case for physically disconneting your primary drive when messing with installing nrew os's.
Dapper appears to have a major fault with this type of setup. I ver leary of Dapper now and if I can ever recover my Breezy drive I will seriouslt start looking for another OS, Dapper has me very scared now. I am not a woos, but I just can't be speding weeks trying to fix something as irresponsible as over writting a partition that was not even included from the choices for the install[-X

---

### Post by zxee on 2006-08-17
How is your bios set up to boot? I think you're suggesting that you sata drive is the 1st drive to boot. In linux though it's usually the 1st ide drive. From the live cd you can do > sudo grub-install hd0
and that should install to the mbr of the ide drive.
If that doesn't work open a terminal and type > sudo fdisk -l
Post the output here.

---

### Post by tbobo05 on 2006-08-17
it hasnt wiped my sata drive...yet....lol. i can still boot to it and it has XP on it.  ive rebooted from live disk and checked the disk partitions for both the hdb and sda drives (ide and sata drives, respectively), and all seems to be good.  i just dont think that it installed it's bootloader to the sata bootsector (since that is which harddrive that is checked at bootup). of course, after what you just said, im not exactly sure that i want to....

---

### Post by zxee on 2006-08-17
From the live cd you can use that fdisk command to see how it's all layed out. Installing grub won't wipe out your install, but it could temporily prevent you from booting into anything. Have a look at smart boot manager [http://btmgr.webframe.org/](http://btmgr.webframe.org/) if you don't want to use grub.

---

### Post by tbobo05 on 2006-08-17
sorry, was already replying to previous reply before i saw yours.  i would like to use grub and here is the output of fdisk 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4664    37463548+  83  Linux
/dev/hdb2            4665        4865     1614532+   5  Extended
/dev/hdb5            4665        4865     1614501   82  Linux swap / Solaris
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        6885    55271632+   7  HPFS/NTFS
/dev/sda3            6886        9301    19406520    7  HPFS/NTFS
/dev/sda4            9302        9725     3405780   db  CP/M / CTOS / ...

---

### Post by zxee on 2006-08-17
Well your ide drive is hd1 (grub counts from 0) your sata drive is hd0
Grub doesn't do "s" for drives. I don't know if installing to your sata will work, but I believe it's the boot drive. Do you have a floppy drive? (probably not)
If you do have a floppy you could have grub install to that > sudo grub-install fd0 and then boot from that. 
There's another bootloader I've used which will boot systems when nothing else will [http://gujin.sourceforge.net/](http://gujin.sourceforge.net/) and I believe you can put it on a cd.
I haven't done that-always used it from floppy. 
Hope that helps. I'm off now-bedtime.

---

### Post by tbobo05 on 2006-08-17
nope sorry, but i do have a little pen drive, can i make that a boot disk?

---

### Post by zxee on 2006-08-17
The installs here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
talk about installing the whole system to a pendrive.
If you can boot from the pendrive, maybe but then you'll probably be changing your bios. Sorry I think I was too enthusiastic-trying to get this working.
I really recommend gujin if you can download it and get it on cd. Otherwise with your setup (sata as 1st boot) I don't know what to do.

---

### Post by tbobo05 on 2006-08-17
changing bios is not a problem.....do i need to formate the pendrive any special way to make it boot or just install the files to it?

the other bootloader you suggested says it doesnt support NTFS :-(   ....im going to try to install grub to the bootsector of the sata drive.....

---

### Post by zxee on 2006-08-17
Changing the bios boot order is a problem. It's not a problem for you to change it of course, but the problem is that after it's changed grub will not see hd1 as hd1 because changing the boot order changed that.
I may be making this more of a problem than it is. 
I'm just not sure if there has been some recent change in booting from sata drives-it could work to install grub to the mbr of the sata drive is what I'm saying. Let me check before I leave and if I find a howto for sata here at ubuntu I'll add it here.

---

### Post by zxee on 2006-08-17
I decided to just do a new reply. 
There's a thread here [http://www.ubuntuforums.org/showthread.php?t=236686&highlight=grub+sata](http://www.ubuntuforums.org/showthread.php?t=236686&highlight=grub+sata) 
that sort of confirms what I said i.e. sata drives don't always get seen correctly (out of order)
But in installing grub you are not doing anything but changing your mbr If anything goes wrong you can use the dos command fdisk /mbr (you'll have to search that-my dos is dusty) to recover the orginal set up. 
You've already determined that your win and linux installs are there. If the > sudo grub-install hd0 doesn't work right you can bring your orginal mbr back or you can use the live cd to look at and edit /boot/grub/menu.lst Search for grub & menu.lst 
Hope that helps.

---

### Post by zxee on 2006-08-17
> **tbobo05 said:**
> changing bios is not a problem.....do i need to formate the pendrive any special way to make it boot or just install the files to it?

the other bootloader you suggested says it doesnt support NTFS :-(   ....im going to try to install grub to the bootsector of the sata drive.....

Let the thread know how that goes. Hope it's good news :)

---

### Post by tbobo05 on 2006-08-17
ok, im trying to install to bootsector of sata drive now....will let you know


i get 

"could not find device for /boot: Not found or not a block device."

after running sudo grub-install hd0

---

### Post by elizleisndahizle on 2006-08-17
If you are trying to fix the mbr so you can start up Windows just put in your windows cd and hit when it asks you if you want to go into recovery mode or whatever and in the "recovery console" type fix mbr

that should fix your windows master boot record but you wouldn't be able to get into ubuntu anymore.

---

### Post by tbobo05 on 2006-08-17
thats the thing, it never installed the bootloader into the same mbr as windows.  i can boot windows just fine, its just that GRUB wasnt installed there for me to have the choice to boot  into linux. now when i try to "sudo grub-install hd0" i get a "no device" error.  is there some way else to do it?

---

### Post by tbobo05 on 2006-08-17
i know this is probably not the place to ask this, but i figure one of you bright fellows may be able to help me.....

is there a way to add a entry to the Win XP bootloader to make it point to the second harddrive?  i know grub is already installed on the 2ed drive with my linux partitions and if i could point it there then maybe grub would take over

---

### Post by zxee on 2006-08-17
This howto seems reasonably complete [http://www.highlandsun.com/hyc/linuxboot.html](http://www.highlandsun.com/hyc/linuxboot.html)
see if that will work for you, and if not the option remains to try and get grub working.

And this from the gentoo site is more complete with better reference to grub:
[http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why](http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why)

---


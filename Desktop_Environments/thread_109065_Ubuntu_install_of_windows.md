---
title: "Ubuntu install of windows"
date: 2005-12-27
forum: Desktop Environments
---

### Post by Doc504 on 2005-12-27
If I just have ubuntu os on my computer, what steps would I use in :confused: order to install wins98/2d?  I have the old wins 98 cd.
Thanks.

---

### Post by lrmall01 on 2005-12-27
Well, let me start off by saying that I've never actually done this - so use your own judgement.  I have re-installed windows 98 on a dual boot machine - which not exactly what your wanting to do.

Anyway, the procedure should be much like installing Linux when you already have Windows installed.

1 - create a partition for windows (maybe need format it as fat)
2 - install windows
3 - boot back into Linux with some type of rescue disk or cd and reconfigure grub

A few notes about the comments above.  In step 1, I think windows will have to have the first partition on the disk.  I'm not sure that the windows boot loader can skip to later sections of the disk.  In other words, make your partition for windows hda1.  Here's what my partitions look like:

Disk /dev/hdb: 45.0 GB, 45020602368 bytes
16 heads, 63 sectors/track, 87233 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30473    15358108+   c  W95 FAT32 (LBA)
/dev/hdb2           30474       44036     6835752   83  Linux
/dev/hdb3           44037       87233    21771288    f  W95 Ext'd (LBA)
/dev/hdb5           44037       45919      949000+  82  Linux swap / Solaris
/dev/hdb6           45920       87233    20822224+  83  Linux

Step 3 is necessary because windows will take over the MBR and clear whatever grub has put there.  After you install windows and restart, your machine will go directly to windows without giving you the chance to start linux.  You'll need to boot from floppy or cd to rerun grub.

Hope this helps.

---

### Post by Doc504 on 2005-12-29
Thank you for that help.
I was wondering if I could uninstall ubuntu than reinstall wins98/2d.  After that use the ubuntu cd that allows one to install ubuntu along with wins98?  How do I uninstall ubuntu?  I hope that I can than re-install ubuntu along with that wins98 os??:confused: 
Happy New Year!:p 
Doc

---

### Post by Sef on 2005-12-30
To install Windows 98, it has be be on the first partition.  It is easier if 98 is on first, then install Ubuntu.  Windows likes to take over the whole disk, so it will end erasing the operating system(s) that are the disk.  

Easiest install:  Install Windows 98 then install Ubuntu.   

Hardest:  Set up a partition for 98 and install it there.   Look up some posts on how to do it.

If you want to delete the Ubuntu partitions before installing 98,  start up the live CD, go to applications -----> System Tools ------> gparted.  It is a partitioner that is gui based.

When installing Ubuntu, make sure that Windows 98 remains bootable, and Ubuntu root is not bootable.

---


---
title: "Ubuntu 10.04 w/ Virtualbox running corporate WindowsXP partition"
date: 2010-08-12
forum: Desktop Environments
---

### Post by cocamoxb on 2010-08-12
Hello all. I've received my corporate laptop with WindowsXP and I installed Lucid "along side" WindowsXP so that I could maintain my corporate image. I was going to use Acronis to take the XP partition and convert it to a VirtualBox VM but I don't want to spend $$ on that. I also would like to be able to maintain my ability to dual-boot.

So......

I've followed all the steps in the links below, and Googled, and search for loose change. I've got as far as getting the guest to start up and all it does is show a black screen with "MBR" with the blinking cursor after it and then the cursor goes down one line and that is where it sits indefinitely. 

Here are the main links I referenced while constructing this beast.

[http://blog.amhill.net/2010/01/27/linux-ftw-using-virtualbox-with-an-existing-windows-partition/](http://blog.amhill.net/2010/01/27/linux-ftw-using-virtualbox-with-an-existing-windows-partition/)

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)




With all that, I still can't figure it out. So here is the output of the pertinent commands:


fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29112ab2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       11125    84092548    7  HPFS/NTFS
/dev/sda2           11125       20674    72188929    5  Extended
/dev/sda5           11125       20279    69201920   83  Linux
/dev/sda6           20279       20674     2985984   82  Linux swap / Solaris




VBoxManage internalcommands listpartitions -rawdisk /dev/sda


Oracle VM VirtualBox Command Line Management Interface Version 3.2.8
(C) 2005-2010 Oracle Corporation
All rights reserved.

Number  Type   StartCHS       EndCHS      Size (MiB)  Start (Sect)
1       0x07  1   /0  /1   1023/239/63         82121        15120
5       0x83  1023/239/63  1023/239/63         67580    168202240
6       0x82  1023/239/63  1023/239/63          2916    306608128




install-mbr --force .VirtualBox/winxp.mbr

ll .VirtualBox/winxp.mbr 
-rw-r--r-- 1 user group 512 2010-08-11 13:05 .VirtualBox/winxp.mbr


VBoxManage internalcommands createrawvmdk -filename /home/<username>/.VirtualBox/winxp.vmdk -rawdisk /dev/sda -partitions 1 -mbr ~/.VirtualBox/winxp.mbr -relative -register

---

### Post by cocamoxb on 2010-08-26
Anyone? I'd be very grateful for any assistance that may come of this. Thank you.

---

### Post by cocamoxb on 2010-09-09
I tried running:

VBoxManage internalcommands createrawvmdk -filename  /home/<username>/.VirtualBox/winxp.vmdk -rawdisk /dev/sda  -partitions 1 -relative -register 	

instead of:

VBoxManage internalcommands createrawvmdk -filename  /home/<username>/.VirtualBox/winxp.vmdk -rawdisk /dev/sda  -partitions 1 -mbr ~/.VirtualBox/winxp.mbr -relative -register 	

which then allows Virtualbox to boot up but it gets to selecting Ubuntu or XP and just hangs.


Any advise would be appreciated. Thank you.

---


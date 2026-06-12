---
title: "Changing Partitions"
date: 2009-03-23
forum: General Help
---

### Post by john@ukgillies.com on 2009-03-23
Hello everyone,

I am new to Linux, and am delighted with my experience so far.

I have been experimenting with Kubuntu and have been adding and testing different installations.
I now have an installation that works and I like. However...I now have a bit of a mess on my hard drive.

See attached screenshot from QtParted - snapshot1.png
The working installation is on sdb5. I use GRUB as the bootloader for both Linux and an old windows installation on sda1 which is also the boot disk.

However Linux is on a logical partition. I would like to clear the disk and have one partition with my installation and dump the rest.

Questions:-
[LIST=1]
[*]Can I do this without losing my installation?
[*]If so, how?
[/LIST]

FDISK output looks like

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5022    40339183+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007f0b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9288    74605828+  83  Linux
/dev/sdb2            9289       38913   237962812+   5  Extended
/dev/sdb5           27621       36290    69641743+  83  Linux
/dev/sdb6           36291       36664     3004123+  82  Linux swap / Solaris

Many thanks for any help.

John

---

### Post by stalkingwolf on 2009-03-23
Im thinking your best bet might be to use remastersys and make an image of your system you want to keep, then just reformat and reinstall it.

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

is a place to start

---

### Post by john@ukgillies.com on 2009-03-23
Many thanks for this.
There is just so much free good software out there!

I wondered about using Pmagic, but messing about with partitions is scary and I would only do this after taking a backup.

Your suggestion makes the backup easy too.

Thanks again.

---


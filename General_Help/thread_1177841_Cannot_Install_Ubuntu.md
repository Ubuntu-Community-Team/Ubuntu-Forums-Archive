---
title: "Cannot Install Ubuntu"
date: 2009-06-03
forum: General Help
---

### Post by Kaorichan2009 on 2009-06-03
I can't install Ubuntu because of a: no root file system error.
Its a new hard drive inside a Gateway Essential. The Hard Drive I believe came out of a Dell optiplex 150? My friend just installed more ram and a new hdd So im not absolutely sure of whats in this computer... I know theres only a CD drive and the floppy was taken out. Is there a way I can install Ubuntu or is the computer a lost cause? (I also have Fedora.)

---

### Post by michy99 on 2009-06-03
Do you have the Ubuntu install CD? Can you boot from it?

---

### Post by Kaorichan2009 on 2009-06-03
I can boot from the CD but I want to install it.

---

### Post by michy99 on 2009-06-03
From the Live CD, enter```
sudo fdisk -l
``` in a terminal and post the output.

---

### Post by Kaorichan2009 on 2009-06-03
im in live disk now and using firefox... heres the info.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26        4851    38752984    b  W95 FAT32

---

### Post by Kaorichan2009 on 2009-06-04
I didnt know which one to post.

---

### Post by Jammy4041 on 2009-06-04
sudo fdisk -l , as in -l for lemonade; you were writing -1.

Do you want to take up all the hard drive? If so, select "Guided Partitioning - Use Entire Disk" as your option. Do not use Manual Partitioning. 

If you want to partition your hard drive, do it like this, (I'm assuming you want to dual boot):

Open gParted. Resize existing Partition, so that there's room for Ubuntu. Do not create a swap partition.  Click apply.

Once finished, open the Ubuntu installer, and select "Use largest Continuous Free Space". Install. 

Hope this helps.

---

### Post by Kaorichan2009 on 2009-06-04
Will this fix the problem? Well the root problem... I want triboot Fedora Ubuntu and 98... l 1 T_T they look the same on windows lol

---

### Post by Kaorichan2009 on 2009-06-04
What is gParted? And it still comes up with the root problem even though im changing the partitions... I have a book here but its a little old and for redhat. D: but its talking about fdisk partitioning.

---

### Post by Kaorichan2009 on 2009-06-06
Apperently i need to use the full hard drive... i hope i can put Fedora on it then~ All and All its fixed.

---


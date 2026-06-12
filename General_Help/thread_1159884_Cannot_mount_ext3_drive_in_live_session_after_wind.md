---
title: "Cannot mount ext3 drive in live session after windows install"
date: 2009-05-15
forum: General Help
---

### Post by geoffreyalgar on 2009-05-15
(FIRST POST: ADVICE ON POSTING/PROTOCOL APPRECIATED)

I recently installed Windows 7 on the second hard drive of my computer (the first holds Crunchbang 8.04). Windows works fine and knocked out GRUB as per usual. However once repairing GRUB, I could not boot into **or even mount the Crunchbang drive in a live session**.




Terminal session with relevant information:
NOTE: /dev/sdc is the 1gb USB live stick

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

crunchbang@crunchbang:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8bda8bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38213   306944000    7  HPFS/NTFS
/dev/sda2           38214       38913     5622750    5  Extended

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65c43fb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

Disk /dev/sdc: 1027 MB, 1027416576 bytes
32 heads, 62 sectors/track, 1011 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Disk identifier: 0x8ef631df

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     1064787     2052059   979374166   66  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(734, 123, 14) logical=(1064786, 10, 21)
Partition 1 has different physical/logical endings:
     phys=(120, 143, 6) logical=(2052058, 21, 22)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?     1738586     3726659  1972168331    7  HPFS/NTFS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(187, 180, 14) logical=(1738585, 4, 52)
Partition 2 has different physical/logical endings:
     phys=(784, 0, 13) logical=(1561856, 0, 1)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?     1653132     2637739   976730017   7d  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(252, 59, 46) logical=(1653131, 28, 39)
Partition 3 has different physical/logical endings:
     phys=(139, 118, 4) logical=(472936, 22, 28)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?     1197222     1201417     4161546+  6f  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(370, 101, 50) logical=(1197221, 5, 11)
Partition 4 has different physical/logical endings:
     phys=(10, 114, 13) logical=(1201416, 8, 37)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
crunchbang@crunchbang:~$ sudo mkdir /mnt/cbang0
crunchbang@crunchbang:~$ sudo mount -t ext3 /dev/sdb1 /mnt/cbang0
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

crunchbang@crunchbang:~$ dmesg | tail
[  116.440419] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 1920 not in group (block 808464432)!
[  116.440868] EXT3-fs: group descriptors corrupted!
[  116.472689] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 1920 not in group (block 808464432)!
[  116.472708] EXT3-fs: group descriptors corrupted!
[  119.654422] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 1920 not in group (block 808464432)!
[  119.654871] EXT3-fs: group descriptors corrupted!
[  119.686307] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 1920 not in group (block 808464432)!
[  119.686325] EXT3-fs: group descriptors corrupted!
[  189.037867] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 1920 not in group (block 808464432)!
[  189.038330] EXT3-fs: group descriptors corrupted!
crunchbang@crunchbang:~$

---

### Post by brianafischer on 2009-05-17
I have the same problem after installing Win 7 RC1.  Hopefully I can find a solution, but it appears that Win7 somehow corrupted the ext3 linux partition.  I hope this malicous behaviour is not intentional on Microsofts part, that would just be evil.

---

### Post by geoffreyalgar on 2009-05-18
Problem solved. fsck /dev/sdb1 and rebooted. The ext3 drive mounted with no issue and grub booted as normally.

---


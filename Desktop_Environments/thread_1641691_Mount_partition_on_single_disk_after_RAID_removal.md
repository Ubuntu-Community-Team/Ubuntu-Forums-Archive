---
title: "Mount partition on single disk after RAID removal"
date: 2010-12-09
forum: Desktop Environments
---

### Post by hadaxu on 2010-12-09
I had RAID 1 with two identical SATA hard drive configured by CMOS on a Dell desktop. After reinstallation of Ubuntu, I remove RAID to get more space and install the OS on the first hard drive and leave the 2nd one intact.

The problem is I cannot mount one of the partitions in the 2nd hard drive, which is /dev/sdb4. I can mount sdb1,sdb2,sdb3 flawlessly.

The command I use is:

**sudo mount -t ext3 /dev/sdb4 /mnt/sdb4**

(I know /dev/sdb4 was formatted as ext3).

Error I got:
===========================
mount: wrong fs type, bad option, bad superblock on /dev/sdb4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
===========================

Here is the disk partition information:

======================================================
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          15      120456    6  FAT16
/dev/sdb2   *          16          28      102400    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdb3              28        6390    51097600    7  HPFS/NTFS
/dev/sdb4            6391       60801   437056357+   5  Extended
/dev/sdb5   *        6391       58594   419328598+  fd  Linux raid autodetect
/dev/sdb6           58595       60801    17727696   fd  Linux raid autodetect
======================================================

Please advice. Thanks.

---

### Post by hadaxu on 2010-12-09
Just figured out the /dev/sdb4 is an extended partition. The one I need is /dev/sdb5. Mounted.

---


---
title: "Just 1 HDD missing from Places --&gt; Computer"
date: 2008-06-10
forum: Desktop Environments
---

### Post by anth on 2008-06-10
Hi all.

I have 4 HDDs in my computer, /dev/sda to /dev/sdd.  They all show up nicely in Places --> Computer (unmounted by default when I boot up), except for just one, /dev/sdb.

However, if I go to a terminal window, and mount it manually (sudo mount -t ntfs /dev/sdb /media/sdb), i can access it fine. It even shows up in "Computer" after I've mounted it, but disappears after I unmount it.

What I really want is for the icon to remain in "Computer" when it's unmounted, like the rest of my hard drives.

How does Ubuntu populate the "Computer" display? is there some kind of /etc/gnome/optionalmounts.fstab file or something?

Ok, I'm going to paste in some outputs, which will show that my /dev/hdb is somehow set up as a 1-disk RAID. Now, I know the urge is almost irresistible to completely ignore the questions I've asked above, and focus solely on fixing this "1-disk RAID" problem. But I'm asking you to resist that urge. Ignore the 1-disk RAID problem, because it's obviously not a show stopper (because I can still mount the disk manually) - what I really want to know and understand is how to force a non-automatically-discovered disk icon into "Computer", or if that's even possible at all.

Cheers

```
$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x87618761

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/sda2            1959        4904    23663745    5  Extended
/dev/sda3            4905       30401   204804652+   7  HPFS/NTFS
/dev/sda5            1959        4776    22635553+  83  Linux
/dev/sda6            4777        4904     1028128+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?       13578      119522   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sdb4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11221121

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3d80

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS
```
```
$ sudo mkdir /media/sdb
$ sudo mount /dev/sdb /media/sdb
mount: unknown filesystem type 'nvidia_raid_member'
$ sudo mount -t ntfs /dev/sdb /media/sdb
$ ls /media/sdb
Apps  Downloads  eBooks  Games  Images  Music  old_c_drive.zip  Podcasts  RECYCLER  System Volume Information  Thumbs.db  Programs  Video 1  Video 2  Working
```
```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0967b58a-920b-4af7-9937-742830efc1a0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=ae65163f-041f-48d3-95a0-ab02e1a1dbba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
I notice that none of my hard drives except the ubuntu "/" and swap are in my fstab, which is fine by me because I don't want the mounted by default at boot time.

---


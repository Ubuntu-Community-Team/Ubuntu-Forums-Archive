---
title: "Help Mounting Slave Drive"
date: 2008-12-16
forum: General Help
---

### Post by revolutionaction on 2008-12-16
So I need some personal help getting a slave drive mounted. I've been using linux for a bout a year, started with xubuntu, moves to ubuntu and now back to xubuntu due to some recent corruption of my ubuntu system. Anyways, a few months ago I installed a new slave drive thats 120 gbs, and under ubuntu it just popped up into my /media/ and my desktop and all I have to do was right click and select 'mount' and from then on it was always mounted. Now with this switch over to xubuntu I cant seem to get it going, and I'm eager to get this hd mounted so I can hurry up and get my torrent for my private tracker hosted. 

Heres my fdisk -l

```
josh@revolutionaction:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3b0bbe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f6534ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

```

and here is my cat /etc/fstab

```
josh@revolutionaction:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=08bb1b45-0658-4713-bd8e-cc14ed19cb17 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=29078a02-7a71-435a-b4a0-d070b4a122fb none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

and finally Blkid

```
josh@revolutionaction:~$ blkid
/dev/sda1: UUID="08bb1b45-0658-4713-bd8e-cc14ed19cb17" TYPE="ext3" 
/dev/sda5: UUID="29078a02-7a71-435a-b4a0-d070b4a122fb" TYPE="swap" 
/dev/sdb1: UUID="E8D0B3A9D0B37BFE" LABEL="Josh Music" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

```


Its noticing that the hd is named Josh Music, and that its ntfs, I'm just wondering what I add to my fstab to get this mounted. Thanks in advance!

---


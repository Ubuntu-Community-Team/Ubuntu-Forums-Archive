---
title: "mounting files and disks"
date: 2005-12-21
forum: General Help
---

### Post by tronsmo on 2005-12-21
first of all - Excuse me if my english stinks.

I might have done something wrong when installing Ubunti Breezy Badger. I`ll try to explain why I think so.

When starting Ubuntu there is a long list of checks wich all is completed ok. But there is this "mounting local files" or something that allways comes with error.

I didn`t know what hda1 and so on was, but I was explained that I could reach my windows-files through these. I run dualboot. I was also explained how to get access to those.

So I run Terminal and this is what happens:
alf@aiubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/hda5            1276        1339      514048+   7  HPFS/NTFS
/dev/hda6            1340        5959    37110118+   7  HPFS/NTFS
/dev/hda7            8989        9728     5944018+   7  HPFS/NTFS
/dev/hda8            5960        8988    24330411   83  Linux

Partition table entries are not in disk order
-------------------

So. What do I do?     :confused:

---

### Post by tlc on 2005-12-21
Can you post the contents of your /etc/fstab file? Does everything work despite the error you see on boot?

---

### Post by tronsmo on 2005-12-21
[QUOTE=tlc]Can you post the contents of your /etc/fstab file? Does everything work despite the error you see on boot?[/QUOTE]

Shure. Everything else seems to work just fine. There are some small issues but that is about my own knowledge...  :D 

Here are the content of the fstab-file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hda6       /media/hda6     ntfs    defaults        0       0
/dev/hda7       /media/hda7     ntfs    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda6       /media/windows  ntfs    nls=utf8,umask=0222 0       0

---

### Post by tronsmo on 2005-12-21
[QUOTE=tronsmo]
I might have done something wrong when installing Ubunti Breezy Badger.[/QUOTE]

Am I right when I believe that this is because something was incorrectly done during the installation?

---


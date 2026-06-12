---
title: "Mounting files and drives"
date: 2005-12-26
forum: General Help
---

### Post by tronsmo on 2005-12-26
I try once again after I didn`t get many replies in my first post:

I might have done something wrong when installing Ubunti Breezy Badger. I`ll try to explain why I think so.

When starting Ubuntu there is a long list of checks wich all is completed ok. But there is this "mounting local files" or something that allways comes with error.

I didn`t know what hda1 and so on was, but I was explained that I could reach my windows-files through these. I run dualboot. I was also explained how to get access to those.

So I run Terminal and this is what happens:

"alf@aiubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1275 10241406 7 HPFS/NTFS
/dev/hda2 1276 9728 67898722+ f W95 Ext'd (LBA)
/dev/hda5 1276 1339 514048+ 7 HPFS/NTFS
/dev/hda6 1340 5959 37110118+ 7 HPFS/NTFS
/dev/hda7 8989 9728 5944018+ 7 HPFS/NTFS
/dev/hda8 5960 8988 24330411 83 Linux

Partition table entries are not in disk order"

----
I was asked what the content of my /etc/fstab-file was, and here it is:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda8 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 ntfs defaults 0 0
/dev/hda5 /media/hda5 ntfs defaults 0 0
/dev/hda6 /media/hda6 ntfs defaults 0 0
/dev/hda7 /media/hda7 ntfs defaults 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda6 /media/windows ntfs nls=utf8,umask=0222 0 0

---

### Post by zoiks on 2005-12-26
I'm not exactly sure why you are getting errors, but I would note that you have a slightly unusual arrangement of partitions.  You have 5 ntfs partitions: hda1, 5, 6, and 7.  I don't know how many Windows's you have installed, but presumably you have one in hda6.  The partition hda2 looks like it's just an extended partition, within which hda's 5-8 live.  For some reason you don't have a Linux swap partition, so you may be using a swap file.  FWIW you will get better performance with a swap partition.

Another thing is hda8 occurs before hda7.  I don' think there's anything wrong with that, but it shows you've been manipulating the partitions.  But why you would add yet another NTFS partition after making a Linux partition?.

I wonder if one of your partitions is mislabeled, e.g. maybe one of your NTFS partitions as listed here maybe is supposed to be your swap partition or something else.  Do you remember how you intended to arrange your partitions?

---

### Post by tronsmo on 2005-12-27
[QUOTE=zoiks]
I wonder if one of your partitions is mislabeled, e.g. maybe one of your NTFS partitions as listed here maybe is supposed to be your swap partition or something else.  Do you remember how you intended to arrange your partitions?[/QUOTE]

This makes sence in a way. I remember trying to make a swap-partition, but I didn`t really understand the GUI. Seems like theres been something wrong there.
So how do I correct this? Reinstall both win xp and Ubuntu?

---


---
title: "Change name of mounted partitions"
date: 2006-10-22
forum: Desktop Environments
---

### Post by LTBookman on 2006-10-22
Hi, I have two partitions mounted, in /media/windows and /media/datos, but, don't know why, they appear on my desktop and in "places" as "Windows" and "DATOS". Why is the capitalization? Is there any way to change that, especially the all caps annoying thing?

TIA.

Just in case, fstab looks as follows:

[QUOTE=/etc/fstab]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4 -- converted during upgrade to edgy
/dev/hda4 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda2 -- converted during upgrade to edgy
/dev/hda2 /home ext3 defaults 0 2
# /dev/hda1 -- converted during upgrade to edgy
/dev/hda1 /media/windows ntfs defaults,auto,nls=utf8,umask=0222 0 0
#/dev/hdb5       /media/datos     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb5 -- converted during upgrade to edgy
/dev/hdb5 /media/datos vfat defaults,rw,user,auto,iocharset=utf8,umask=0 0 0
# /dev/hda5 -- converted during upgrade to edgy
/dev/hda5 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0[/QUOTE]

---


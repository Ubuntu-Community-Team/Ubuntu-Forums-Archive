---
title: "Mounting an NFFS partition"
date: 2006-06-09
forum: Desktop Environments
---

### Post by canadianwriterman on 2006-06-09
I'm trying to automount my NTFS partition, but without success. I have a single HD and NTFS is on partition 2. I edited fstab as follows and then rebooted:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda9       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda10      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda2	/media/Windows	ntfs	nls=utf8,umask=0222	0	0

When I open the Media directory and open the Windows subdirectory, it is empty. Any ideas? Thanks.

EDIT: Sorry, I solved my problem. I had mistyped the folder name in /media. I corrected it and now see my NTFS drive.

---


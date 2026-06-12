---
title: "change ownership of mounted fat32 paritions"
date: 2006-08-31
forum: Desktop Environments
---

### Post by rkakkar on 2006-08-31
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /media/hda4     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda7       /media/hda7     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


current for hda4, hda5, hda6 and hda7, its showing the owner as 'root'. I want to change that to a user account. how can i do so?

---

### Post by xyz on 2006-08-31
Hi-
There's a nice explanation of what all these permission-related **uid=1000, sync,umask=0077, umask=0277, ro, nls=utf8 ** and what to do with them...for a start, it's always nice to understand that.
You'll find it under the 'System Configuration' section.

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#MouSystem](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#MouSystem) Configurationnting_drives_and_.2Fetc.2Ffstab

---


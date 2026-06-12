---
title: "My system dont paly dvd"
date: 2006-04-05
forum: Desktop Environments
---

### Post by realdog on 2006-04-05
When i try to see a dvd my system tell me this 
Could not mount device.
The reported error was:
[mntent]: warning: no final newline at the end of /etc/fstab
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
and my etc/ fstab says this
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5     /mnt/windows    vfat,auto  iocharset=utf8,umask=000   0     0  

Please i wan to see many dvds that i burn in another computer.

---


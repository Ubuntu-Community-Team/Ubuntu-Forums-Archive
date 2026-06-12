---
title: "automount fat32 partition"
date: 2007-10-21
forum: Desktop Environments
---

### Post by lizardopulo on 2007-10-21
Hi all, only a simple question.
What's the correct way to automount my fat32 partition?
I've tried to search a little guide but I don't understand how to put the right "type" and "options".

*This is my fstab*

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8b9af8f6-5b8e-4995-a5e8-04721cb0e342 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=00c4028d-1ba6-444b-91da-74b42518cc07 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0


**This is my doubt**
[COLOR="Red"][COLOR="DimGray"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8b9af8f6-5b8e-4995-a5e8-04721cb0e342 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=00c4028d-1ba6-444b-91da-74b42518cc07 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0[/COLOR][/COLOR]
[COLOR="Red"]/dev/sda3        /media/storage   vfat defaults,user,rw,exec 0       0[/COLOR]

Many thanks to someone who can explain or give a link to a simple guide

---

### Post by aysiu on 2007-10-21
This should help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

After you make sure the /media/storage directory exists, the line in your /etc/fstab should be ```
/dev/sda3 /media/storage vfat iocharset=utf8,umask=000 0 0
```

---


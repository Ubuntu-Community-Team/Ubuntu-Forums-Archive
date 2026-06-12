---
title: "lost harddrive, &quot;You do not have permissions&quot;"
date: 2006-08-13
forum: Desktop Environments
---

### Post by onlybui on 2006-08-13
I'm trying to remount my harddrive and it gives me a error that I have no permissions...


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda9       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda10      none            swap    sw              0       0

/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

I removed from fstab "/dev/sdb5    /media/sdb5   ext2  defaults, errors=remount -ro 0 1"
and Still I get this error message when I try to mount from the gui from system...

any idea how to auto mount

---

### Post by skale on 2006-08-13
have you done it with sudo?

---

### Post by onlybui on 2006-08-13
From the gui SYSTEM I have to enter sudo password so yes...?

---


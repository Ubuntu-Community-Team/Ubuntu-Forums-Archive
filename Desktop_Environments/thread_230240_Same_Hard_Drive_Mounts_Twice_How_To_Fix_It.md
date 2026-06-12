---
title: "Same Hard Drive Mounts Twice How To Fix It?"
date: 2006-08-05
forum: Desktop Environments
---

### Post by magnoliablossom on 2006-08-05
I wanted my 2nd hard drive to mount on start up so I followed the wiki Dapper instructions to do it.  Now it's showing up twice on my desktop and in Places under Computer.  I know it's probably not that big of a deal to a lot of people but I'm a neat freak and I can't stand my desktop cluttered.  How can I fix this.  I've rebooted a couple of times but it stays there.  Here's a copy of the file the tutorial told me to edit.  Thanks in advance!

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
dev/hdb1    /media/windows vfat  iocharset=utf8,umask=000  0    0

---

### Post by roostishaw on 2006-08-05
Mabey there should be a foward slash before "dev" on the last line?

---

### Post by magnoliablossom on 2006-08-05
well....duh! lol   thanks.  i didn't notice that.

yup...that worked.  thanks again.

---


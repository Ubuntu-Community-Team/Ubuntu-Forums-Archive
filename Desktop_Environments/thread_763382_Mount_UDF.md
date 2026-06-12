---
title: "Mount UDF"
date: 2008-04-22
forum: Desktop Environments
---

### Post by dontgetshocked on 2008-04-22
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cb511b8b-fadd-455b-8416-5fe8c638f8bf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=051ae556-c9d3-4f88-b7ea-ed35e174f7bf none            swap    sw              0       0
/dev/hda        /media/cdrom0    udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1    udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
# mount -t udf /dev/scd0/media/cdrom0
# mount -t udf /dev/hdd/media/cdrom1
# /dev/scd0        /media/cdrom0    udf,iso9660 user,noauto,exec 0       0

As you can see, here is my fstab.I need to mount a cdr disk that my sister sent which of course she uses vista.Tried several things with no luck.I have udf tools installed but dont  know how to use them or even where to find them.

Thanks,

Dave

---


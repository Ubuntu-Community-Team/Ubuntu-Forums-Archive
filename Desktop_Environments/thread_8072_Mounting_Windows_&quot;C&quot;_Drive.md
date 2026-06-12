---
title: "Mounting Windows &quot;C&quot; Drive"
date: 2004-12-13
forum: Desktop Environments
---

### Post by elder68 on 2004-12-13
In all the other distro's that I have tried I have been able to access Windows from the desktop of that particular distro. This does not seem to be the situation with Ubuntu.
Could someone kindly point me in the right direction. /etc/fstab file follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I presume that /dev/hda1 is the fat32 partition. Is there a utility that I can use to verify this?

Thank you,

Bill.

---

### Post by davegod75 on 2004-12-13
[QUOTE=elder68]In all the other distro's that I have tried I have been able to access Windows from the desktop of that particular distro. This does not seem to be the situation with Ubuntu.
Could someone kindly point me in the right direction. /etc/fstab file follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I presume that /dev/hda1 is the fat32 partition. Is there a utility that I can use to verify this?

Thank you,

Bill.[/QUOTE]
 check this out

[http://ubuntuguide.org/index.html#mountunmountntfs](http://ubuntuguide.org/index.html#mountunmountntfs)

---

### Post by elder68 on 2004-12-13
[QUOTE=davegod75]check this out

[http://ubuntuguide.org/index.html#mountunmountntfs](http://ubuntuguide.org/index.html#mountunmountntfs)[/QUOTE]

Thank you, that should do the trick!

Bill.

---


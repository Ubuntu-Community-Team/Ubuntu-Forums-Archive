---
title: "Only one DVD drive usable out of two"
date: 2006-07-09
forum: Desktop Environments
---

### Post by Cosmik Debris on 2006-07-09
I have 2 DVD drives in my PC : one Pioneer DVD reader, and one Lite-On DVD burner.

Unfortunately, I can only use one of them : the DVD burner.

I had that problem already in Ubuntu 5.10, but had no time to investigate, but now the same also happens in Ubuntu 6.06 which I just installed one week ago.
When I insert a CD or a DVD into the Pioneer drive, it is just ignored. When I try to mount it manually, it just hangs.

I can successfully boot on the Pioneer DVD reader (that's how I installed Ubuntu), and if I boot up with a non-bootable CD in the drive, it is successfully mounted in Gnome.

One thing I've noticed is that only one CD drive exists in /etc/fstab :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /u01            ext3    defaults        0       2
/dev/hda7       /u02            ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
tmpfs           /dev/shm        tmpfs   defaults        0       0

```

Does anybody have an idea on how to use both drives ?

---

### Post by Cosmik Debris on 2006-07-11
Found the solution (I vaguely remembered doing something similar 1.5 years ago while using Slackware+Dropline Gnome, but didn't remember which files I modified to have it working :( )

Basically, I just had to create /etc/udev/rules.d/10.local.rules with the following 2 lines :
```

BUS="ide", KERNEL="hdc", SYMLINK+="dvd", GROUP="cdrom", MODE="0666"
BUS="ide", KERNEL="hdd", SYMLINK+="dvdrw", GROUP="cdrom", MODE="0666"

```

Incidentally, I also added 2 lines to /etc/fstab, but apparently they are not needed to automount the CDs :
```

/dev/dvd        /media/dvd      udf,iso9660 user,noauto     0       0
/dev/dvdrw      /media/dvdrw    udf,iso9660 user,noauto     0       0

```

Now both DVD drives mount fine

Credits to 
[http://www.ubuntuforums.org/showthread.php?t=168221](http://www.ubuntuforums.org/showthread.php?t=168221)
and [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---


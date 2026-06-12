---
title: "No automount for iPod or CD"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2006-06-03
In Breezy, CDs and my iPod automounted fine.  After the Dapper upgrade - No.  It seems I have the latest version of gnome-volume-manager.

How do I re-enable automount?  

Failing that...can someone point me towards info on how to mount manually?  How do I work out what USB port I'm connecting to?


In case my fstab is relevant:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/hda1	/media/windows	vfat	user,fmask=0111,dmask=0000	0	0

```

---

### Post by dmalinovsky on 2006-06-05
I have similar problem, described [here]("http://ubuntuforums.org/showthread.php?p=1084145").  Please check whether you have gnome-volume-manager process running, AFAIK it should be run (it's my main problem I suspect).

You can try to use usbmount package to mount USB devices automatically.  It's simple command-line application, but it worked for me.

---


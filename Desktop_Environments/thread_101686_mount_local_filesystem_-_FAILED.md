---
title: "mount local filesystem - FAILED"
date: 2005-12-10
forum: Desktop Environments
---

### Post by windowsXuser on 2005-12-10
When Kubuntu is loading and you see the Kubuntu logo and check to see if something is OK or FAILES, i get mount local filesystem FAILED.

Not sure if this is a bad thing, but i can access everything on kubuntu after it loads.

I only started to get this after i tried to install a kde theme and configured the kderc file to include the theme.

But, when i shut down the computer i can see it umoun local filesystem, so, is it getting mounted, i assume so.

blair..

---

### Post by arnieboy on 2005-12-10
[QUOTE=windowsXuser]When Kubuntu is loading and you see the Kubuntu logo and check to see if something is OK or FAILES, i get mount local filesystem FAILED.

Not sure if this is a bad thing, but i can access everything on kubuntu after it loads.

I only started to get this after i tried to install a kde theme and configured the kderc file to include the theme.

But, when i shut down the computer i can see it umoun local filesystem, so, is it getting mounted, i assume so.

blair..[/QUOTE]
paste the contents of:
```
cat /etc/fstab
```

---

### Post by windowsXuser on 2005-12-11
here is the contents of cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by sup on 2005-12-11
i suggest you pay attention also to this thread: [http://www.ubuntuforums.org/showthread.php?t=85885](http://www.ubuntuforums.org/showthread.php?t=85885)

---


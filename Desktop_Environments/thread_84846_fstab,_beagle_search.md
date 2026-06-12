---
title: "fstab, beagle search"
date: 2005-11-01
forum: Desktop Environments
---

### Post by royg1234 on 2005-11-01
Can someone tell me if there's anything wrong with my fstab?  The beagle log file (~/.beagle/Log/current-Beagle) tells me this:

> 05-11-01 03.11.41.27 31860 Beagle WARN: Extended attributes are not supported on this filesystem.  Many search backends will not be available

fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>        <options>                   <dump>  <pass>
proc            /proc           proc          defaults,user_xattr        0       0
/dev/sda3       /               ext3          defaults,user_xattr,errors=remount-ro  0       1
/dev/sda6       none            swap          sw                          0       0
/dev/hdc        /media/cdrom0   udf,iso9660   ro,user,noauto              0       0
/dev/hda        /media/cdrom1   udf,iso9660   ro,user,noauto              0       0
/dev/fd0        /media/floppy0  auto          rw,user,noauto              0       0
/dev/sda1       /mnt/xp         ntfs          nls=utf8,umask=0222         0       0
/dev/sda5       /mnt/files      vfat          iocharset=utf8,umask=000    0       0
/dev/sda4       /mnt/suse       reiserfs      defaults              	  0       0


```

---

### Post by Balki on 2005-11-01
I don't think you should set the extended attributes on the /proc entry.

---


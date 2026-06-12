---
title: "How can i mount my usb stick [XFCE]"
date: 2005-09-04
forum: Desktop Environments
---

### Post by codraider on 2005-09-04
I use Xfce 4.2.1 and i have a memory stick.How can i mount it?
my fstab is
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by kmoffat on 2005-09-04
[QUOTE=codraider]I use Xfce 4.2.1 and i have a memory stick.How can i mount it?
my fstab is
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```[/QUOTE]
 Not sure about xfce, but in debian you can mount an external device using
mount -t vfat /dev/sda1 /mnt/external
if you have created /mnt/external using mkdir.

When I plug in my card reader in ubuntu hoary it automatically shows up as /media/KODAK.

Try 2 things:
Plug in the card and run "ls -l /media" to see if it is there.
Run "tail -f /var/log/messages"; then plug in the drive to see what scrolls. That may show the appropriate device to mount.

---


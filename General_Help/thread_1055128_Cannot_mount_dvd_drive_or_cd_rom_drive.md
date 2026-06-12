---
title: "Cannot mount dvd drive or cd rom drive"
date: 2009-01-30
forum: General Help
---

### Post by don_m on 2009-01-30
I cannot mount either the Memorex DVD ROM drive or the CD reader/writer.

When I look under the file system under media, I have cdrom, cdrom0, cdrom1. I also have a floppy and floppy0.

Here is my fstab file:

[COLOR="Lime"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=63908a60-d0f7-44db-bbb9-52ab630a5cf4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f220c338-36f3-4854-8c8f-8f78e39c9d2f none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# / added by zack later
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0  
# [http://forums.virtualbox.org/viewtopic.php?p=19664&sid=44a581113e4d07e88c46dfdbbd5d1663](http://forums.virtualbox.org/viewtopic.php?p=19664&sid=44a581113e4d07e88c46dfdbbd5d1663)

#/dev/hdb1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb5       /media/fat32sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb6       /media/fat32sdb6     vfat    defaults,utf8,umask=007,gid=46 0       1[/COLOR]

---


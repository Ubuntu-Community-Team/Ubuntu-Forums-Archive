---
title: "Partitions don't show in the media:/ kio_slave"
date: 2005-09-26
forum: Desktop Environments
---

### Post by getaceres on 2005-09-26
I was running KDE 3.4.2 on Ubuntu Breezy preview and I've seen that only CD-ROMS and floppys appear in the media:/ kio_slave.
I tried with KDE 3.5b1 and it's the same. Maybe a hal/dbus bug or is it supposed to be that way?

---

### Post by Paperjam on 2005-09-26
What's the content of your /etc/fstab ?

---

### Post by getaceres on 2005-09-26
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/hdb1     vfat    defaults,umask=000        0       0
/dev/hdb2       /media/hdb2     vfat    defaults,umask=000        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Paperjam on 2005-09-26
If */dev/hdb1* and */dev/hdb2* are the two partitions that are not shown in "media:/", you might want to check if the coresponding mountpoints exist (/media/hdb1 and /media/hdb2). If not, try creating them:
```
sudo mkdir /media/hdb1
sudo mkdir /media/hdb2
```

Here are a few more questions:
- Is there an empty line at the end of you /etc/fstab ? (I remember reading that problems might occur if there is **no** empty line)
- Can you mount the partitions manually? Try:
```

sudo mount /media/hdb1
ls /media/hdb1 *(It should display the contents of that partition)*
sudo umount /media/hdb1 *(to unmount)*

```

---

### Post by getaceres on 2005-09-27
/media/hdb1 and /media/hdb2 exists and the partitions are mounted on boot correctly. I can access to it using the absolute path but not through the media:/ (system:/media in KDE 3.5) kio_slave.
/etc/fstab has a line at the end of it.

---

### Post by Paperjam on 2005-09-27
Try this please: Open the KDE Control Center (kcontrol). Goto Peripherals -> Storage Media -> Advanced and disable "HAL backend". It should work now. If it does, this is probably a bug and you should report it so that it gets fixed for KDE 3.5final.

---

### Post by getaceres on 2005-09-27
I've disabled the Hal backend and now I can see my partitions. Thanks.
I'm going to report it to the KDE and Ubuntu developers.

---


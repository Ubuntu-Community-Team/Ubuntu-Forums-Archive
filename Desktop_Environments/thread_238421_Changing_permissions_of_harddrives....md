---
title: "Changing permissions of harddrives..."
date: 2006-08-17
forum: Desktop Environments
---

### Post by OscarGortez on 2006-08-17
I'm sure there's a really easy fix to this, but basicaly I upgraded to Dapper and it automatically mounted my fat32 partions and i can view and read the files but i still don't have full permissions. I can't change or delete them, so i guess i don't have the write permissions...

---

### Post by taurus on 2006-08-17
You can set the permissions to whatever you want in /etc/fstab!  What does your /etc/fstab look like then?

```
more /etc/fstab
```

---

### Post by OscarGortez on 2006-08-17
<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       /media/hdc5     vfat    defaults        0       0
/dev/hdc6       /media/hdc6     vfat    defaults        0       0
/dev/hdd1       /media/hdd1     ntfs    defaults        0       0
/dev/hdc7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2006-08-17
Try modifying your /etc/fstab to make it looks something like this (for your vfat partitions)...

```

sudo gedit /etc/fstab <-- open an editor

```
```

/dev/hdc5 /media/hdc5 vfat defaults,umask=0222 0 0
/dev/hdc6 /media/hdc6 vfat defaults,umask=0222 0 0

```
Save it and reboot...

---

### Post by OscarGortez on 2006-08-17
Ok... i just tried that and when i try to delete something from one of the drives it still says i don't have the permissions..

---

### Post by taurus on 2006-08-17
Did you remember to reboot your machine after modifying your /etc/fstab?

---

### Post by OscarGortez on 2006-08-17
yeah I restarted... and i just did it again for good measure heh...  and my fstab now reads:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       /media/hdc5     vfat    defaults,umask=0222        0       0
/dev/hdc6       /media/hdc6     vfat    defaults,umask=0222        0       0
/dev/hdd1       /media/hdd1     ntfs    defaults        0       0
/dev/hdc7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by taurus on 2006-08-17
Actually, try "umask=0000" not "umask=0222".  The "umask=0222" is for NTFS.  My bad...  :redface:

---


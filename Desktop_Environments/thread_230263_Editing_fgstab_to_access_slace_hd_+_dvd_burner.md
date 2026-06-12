---
title: "Editing fgstab to access slace hd + dvd burner"
date: 2006-08-05
forum: Desktop Environments
---

### Post by metalsam on 2006-08-05
Just checked my fstab file, and it doesnt contain my DVD +- RW or my slave HD (FAT32) containing all my music etc, which could be why I cant access it :P

The slave HD is hdba5 and I dont know what dev my dvd burner is.

What entries should I add to fstab and how do I found out what dev my dvd burner is?

thanks :)

---

### Post by Ocxic on 2006-08-05
here is a copy of my /etc/fstab edit your other drives into the file.

hda pri/master, hdb pri/slave, hdc sec/master, hdd sec/slave
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Dapper--Main-root /               xfs     defaults        0       1
/dev/mapper/Dapper--Main-Storage /Storage        xfs     defaults        0  2
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Dapper--Main-home /home           xfs     defaults        0       2
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

---


---
title: "access win partition without root"
date: 2006-01-30
forum: Desktop Environments
---

### Post by ESPOiG on 2006-01-30
basically i just typed in terminal everytime i wantd to access my windows partition, then i asked in forums how to get it to mount at startup now it mounts at startup but i cant access it unless im running nautilus under root becuase i just get the error message that i dont have permission, i asked around and found sumone who said try and set permissions in windows, to no avail nothin else seemed to work so here is my FSTAB

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/Windows	ntfs	defaults	0	0

dunno what you can make of it but it mounts just doesnt let me access it

---

### Post by RAOF on 2006-01-30
As per [the wiki page]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29"): replace the "defaults" in your ntfs line with "ro,auto,user,fmask=0111,dmask=0000"

---

### Post by ESPOiG on 2006-01-30
thanks it works now

---


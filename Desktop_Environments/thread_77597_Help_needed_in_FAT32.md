---
title: "Help needed in FAT32"
date: 2005-10-17
forum: Desktop Environments
---

### Post by webbie180 on 2005-10-17
Files added to shared partition under FAT32 cant be read.  Windows added can only be seen when I logged in to Windows and vice versa.  
Used this  in the unofficeial guide,
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
Added the required entries.

sudo mount -a

---

### Post by Pablo_Escobar on 2005-10-17
Post your fstab file here, so we can troubleshoot.

---

### Post by webbie180 on 2005-10-17
This is it,

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2	/media/windows	vfat	iocharset=utf8,umask=000   0       0


Thanks

---


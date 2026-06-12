---
title: "GNOME drive mounts disappeared"
date: 2005-11-11
forum: Desktop Environments
---

### Post by awilisch on 2005-11-11
up until just recently the three partition's that I have mounted have shown up on my desktop as drive icons and have been visible under the computer icon. Recently however the drives have disappeared. I know the partitions are still mounted as I can browse to them. i can't think of anything specific I've done to the desktop to make them stop showing up. My fstab is listed below. Under the computer icon I have Floppy 1, CD-RW/DVD Rom and Filesystem. If I put a cd in the drive it automatically mounts and displays an icon on the desktop. 

Any thoughts are greatly appreciated.


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    umask=000        0       0
/dev/hda7       /media/hda7     ntfs    umask=000        0       0
/dev/hdb1       /media/hdb1     vfat    umask=000        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
awilisch@dauntless:/etc$

---Aric

---

### Post by 23meg on 2005-11-12
In the gnome configuration editor see if this key is disabled and enable it if it is: apps/nautilus/desktop/volumes_visible

Also check if gnome-volume-manager is running; see if it is listed with this command ```
ps aux |grep volume
```

---

### Post by awilisch on 2005-11-12
Actually, I should have posted again. I had un-commented the last line in /etc/default/hal to fix the problem with mounted drives not appearing in the Kde desktop. While this fixes that problem in Kubuntu, it breaks the same thing in GNOME. Not really sure why, but oh well. 

The line in /etc/default/hal is 
#DAEMON_OPTS=--retain-privileges

Just fyi for anyone who runs into this issue in the future.
--Aric

---


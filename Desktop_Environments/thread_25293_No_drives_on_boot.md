---
title: "No drives on boot"
date: 2005-04-09
forum: Desktop Environments
---

### Post by gfs on 2005-04-09
Using Kubuntu 5.0.4
On boot-up it does not recognize any drives.  Not even the CD drive.  With Ubuntu it at least found the CD drive.
What am I not doing?

---

### Post by humanity_to_others on 2005-04-09
You should mount the volumes.
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by gfs on 2005-04-10
That did not help.
There are no entries in fstab for hda1, hda2, fd0, or sda drives.

---

### Post by quique on 2005-04-12
Sorry for my english, is not very well. Go to konqueror services, then click on the red flag (services) and then in storage dispositives? (in spanish is Dispositivos de almacenaje), right click on the unit you want (cdrom) and mount. Thats all for units what can be mounted whitout write the fstab.

---

### Post by gfs on 2005-04-14
That didn't work.
Right click on the icon gives error message "can't find /dev/hda2 in /etc/fstab or /etc/mtab".
Same error for hda1, hdd, fd0.

---


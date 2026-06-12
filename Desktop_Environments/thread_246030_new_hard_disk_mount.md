---
title: "new hard disk mount"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Carles Durán on 2006-08-28
I am not able to mount a new hard-disk, it has NTFS format with data stored from Windows XP (images, video, etc.), The hard disk just appear into the administartion tools as /dev/hda5 but. How can I mount this new volume to the desktop.

Please find enclosed a screenshot of the new HD unit

I'm a Linux beginner 

Thanks in advance...

Carlos

---

### Post by divague on 2006-08-28
Open the teminal and create a mount point

sudo mkdir /media/win

then put this:

sudo gedit /etc/fstab

and add this line:

dev/hda5    /media/win ntfs  nls=utf8,umask=0222 0    0

then put:

sudo mount -a

---

### Post by BLTicklemonster on 2006-09-02
> **divague said:**
> Open the teminal and create a mount point

sudo mkdir /media/win

then put this:

sudo gedit /etc/fstab

and add this line:

dev/hda5    /media/win ntfs  nls=utf8,umask=0222 0    0

then put:

sudo mount -a

Same problem and that didn't work for me.

---

### Post by BLTicklemonster on 2006-09-05
found this, not sure if it will do the trick, but I intend to try it tonight:
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

---


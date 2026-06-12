---
title: "DON'T automount an external USB drive"
date: 2009-08-19
forum: Desktop Environments
---

### Post by Keith Hedger on 2009-08-19
Hi hope some one can help with this, I have a number of external firewire and USB drives which all mount on the desktop fine, but I use one for backups only and I would like it to NOT mount until I go to 'Computer' and click it or click it on the nautilus side-bar at which point I would like it to mount normally, I can stop it mounting by putting a bad mount command in the volume properties and then mount it via the command line but that is a bit long winded, any ideas?

---

### Post by sidewalkcynic on 2009-08-19
hey, I think, I finally get to help someone. I had a similar inquiry a way back. But I think it may not work if you want to auto mount everything else.

```
gconf-editor
```

> Apps
 > Nautilus
  > preferences
     >media automount

---

### Post by mcduck on 2009-08-19
> **Keith Hedger said:**
> Hi hope some one can help with this, I have a number of external firewire and USB drives which all mount on the desktop fine, but I use one for backups only and I would like it to NOT mount until I go to 'Computer' and click it or click it on the nautilus side-bar at which point I would like it to mount normally, I can stop it mounting by putting a bad mount command in the volume properties and then mount it via the command line but that is a bit long winded, any ideas?

You could configure the drive in /etc/fstab (using the UUID or the LABEL of the drive, to distinguish it from other removable drives), and set "user" and" noauto" in the mount options.

This should do exactly what you want, the drive shouldn't be mounted by default but clicking it's icon in the file manager would mount it.

Although I wouldn't consider it as backup drive if it's always connected to your computer.. Any power surge or other danger that might break your computer itself could still break the external drive as well, mounted or not. To actually use it for backup purposes you should keep it unplugged and stored safely somewhere else all the times, apart from when you are actually doing backups.

---

### Post by Keith Hedger on 2009-08-20
sidewalkcynic - Sorry but that would apply to all external disks not just one specific disk

mcduck - I tried putting this:```
UUID=5f06838a-480b-4d41-85be-43ba7b2fc133 /media/Maxtor	ext2	user,noauto,exec	0	0
```at the end of /etc/fstab but the drive still auto mounted, I also tried using the label but that didn't work either.

Anyone else?

---

### Post by mcduck on 2009-08-20
> **Keith Hedger said:**
> sidewalkcynic - Sorry but that would apply to all external disks not just one specific disk

mcduck - I tried putting this:```
UUID=5f06838a-480b-4d41-85be-43ba7b2fc133 /media/Maxtor	ext2	user,noauto,exec	0	0
```at the end of /etc/fstab but the drive still auto mounted, I also tried using the label but that didn't work either.

Anyone else?

Try to get the partition to mount correctly using fstab first. When that works, add the "noauto" option. It definitely should work.

edit: I just tested this myself and it works. (also you'll have to reboot after adding the fstab entry)

edit2: one more thing, if you still can't get it to work try using mount point somewhere else than inside /media, for example /mnt..

---

### Post by Keith Hedger on 2009-08-20
The drive will mount from fstab as a normal user (no sudo) so the options are ok but if the mount point is in /media it will automount if the mount point is in /mnt it doesn't automount but it does not appear in 'computer' or on the nautilus sidebar and so I can't click on it to mount it I have to open a terminal and run```
mount /mnt/Maxtor
```

---


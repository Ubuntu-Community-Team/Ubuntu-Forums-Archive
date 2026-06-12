---
title: "/etc/fstab options don't seems to have any effect when using auto and noauto"
date: 2009-06-24
forum: General Help
---

### Post by ozguitarplayer on 2009-06-24
I have two partitions that mount to the desktop when I boot into the system
yet /etc/fstab has the noauto option set for each and if I put a # in front of the line for each drive it make no difference either.
I have been told it's a Gnome issue.

Is there something else that has influence on these setting, like I haven't got the whole picture? I need to control what mounts on startup.

---

### Post by bullgr on 2009-06-24
can you post please the content of fstab?

---

### Post by ozguitarplayer on 2009-06-24
here it is, it's sda3 & sda4

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda3	/media/lapniles ext3	user,noauto	0	0
/dev/sda4	/media/lapheron	ext3	user,noauto	0	0

---

### Post by geirha on 2009-06-24
If you set the mount-point to /mnt/something, then gnome should ignore them. Also, I'd change the last field for those ext3 filesystems to 2 so that the filesystems will be checked during boot.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda3 /[COLOR="Blue"]mnt[/COLOR]/lapniles ext3 user,noauto 0 [COLOR="Blue"]2[/COLOR]
/dev/sda4 /[COLOR="Blue"]mnt[/COLOR]/lapheron ext3 user,noauto 0 [COLOR="Blue"]2[/COLOR]

```

Remember to create the new mount-points.```
sudo mkdir /mnt/lap{niles,heron}
```

I'd also recommend using the filesystems' UUID. See [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by ozguitarplayer on 2009-06-24
many thanks geirha, that's fixed it

---


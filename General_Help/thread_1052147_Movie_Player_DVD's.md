---
title: "Movie Player DVD's"
date: 2009-01-27
forum: General Help
---

### Post by RedSingularity on 2009-01-27
I try to play a DVD in the player and it says "Could not open location; you might not have permission to open the file."  What is this?  Why cant i play my DVD's?  I cant play the DVD's in VLC media player as well.  Any suggestions would be helpful.

---

### Post by mb_webguy on 2009-01-27
It could be that the disk isn't being mounted with the correct permissions.  Please post the contents of /etc/fstab.

---

### Post by RedSingularity on 2009-01-28
Ahh i got it!  I needed to download the correct codecs.  They didn't come with the Ubuntu installation.

---

### Post by SergeantScar on 2009-02-21
i have the same problem as was listed above.. here is my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=02fe1bfa-17fc-41cc-83fc-06dd3e8f08d5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ee626a8c-0dce-48dc-bd33-afb84794880c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

any help would be much appreciated!

---

### Post by handy on 2009-02-21
> **SergeantScar said:**
> i have the same problem as was listed above.. here is my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=02fe1bfa-17fc-41cc-83fc-06dd3e8f08d5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ee626a8c-0dce-48dc-bd33-afb84794880c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

any help would be much appreciated!

You'll find what you need in here:

*_[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)_*

---


---
title: "CD drive keeps opening before login"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Jose Catre-Vandis on 2006-10-04
Here is one for you:

I have an Edubuntu installation running LAMP and ltsp.

I boot it to a gdm login, but do not login.

During the boot process the CD drive opens

Once boot has finished, if I close the drive, the PC has a think, and then opens it again. This exchange has now been going on for hours.

Any clues as to what is doing this, and how to fix it?  :confused:

---

### Post by dcstar on 2006-10-05
> **Jose Catre-Vandis said:**
> Here is one for you:

I have an Edubuntu installation running LAMP and ltsp.

I boot it to a gdm login, but do not login.

During the boot process the CD drive opens

Once boot has finished, if I close the drive, the PC has a think, and then opens it again. This exchange has now been going on for hours.

Any clues as to what is doing this, and how to fix it?  :confused:

Post your /etc/fstab file, and tell us what the CD drive is set up as (Master/Slave, Primary/Secondary IDE).

---

### Post by Jose Catre-Vandis on 2006-10-06
Here is the fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/music    ext3    defaults        0       2
/dev/hda7       /media/backup ext3    defaults        0       2
/dev/hda8       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc5	/media/apps	ext3	defaults	0	2
/dev/hdd5	/media/vids	ext3	defaults	0	2

```
I've not fiddeld with the fstab apart from loading up the 2nd and 3rd hard
 drives

The drive is slave on the Primary IDE. its just a CD drive (no DVD or writing function)

I stuck a data cd in and closed, this has kept the drive shut for now!

---


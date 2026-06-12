---
title: "after updating..."
date: 2005-12-25
forum: General Help
---

### Post by metuwi on 2005-12-25
edit: so sorry, i see this has already been discussed:
[http://www.ubuntuforums.org/showthread.php?t=79204](http://www.ubuntuforums.org/showthread.php?t=79204)

hi all, 
My hard drives have disappeared from Storage Media after upgrading.

i did [FONT="Courier New"]apt-get update[/FONT] and [FONT="Courier New"]apt-get upgrade[/FONT]
(i included the kde3.5 repository). after finishing the upgrade, i rebooted. everything works fine except:

i have two hard drives. they have disappeared from media:/ and from the desktop (they were there before the upgrade.)

all i find in storage media is the floppy and cd drive, and if i do a [FONT="Courier New"]kdesu konqueror[/FONT], there is nothing in media:/
i can still access the hard drives by going to their mount points, and my fstab is OK. 

my question is, How can i get them back into Storage Media?

this is my fstab:
[FONT="Courier New"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1       /media/hd2      vfat    iocharset=utf8,umask=000 0 0
[/FONT]

thanks!

---


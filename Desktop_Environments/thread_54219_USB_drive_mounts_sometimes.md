---
title: "USB drive mounts *sometimes*"
date: 2005-08-03
forum: Desktop Environments
---

### Post by filemanager on 2005-08-03
I have a USB drive, and when I reboot my computer and Linux starts up, my USB drive is mounted and the icon is on the desktop - sometimes. But lately, it won't mount at all, and I'm not sure how to mount a drive manually. Can anyone help?

---

### Post by autocrosser on 2005-08-03
What 's your /etc/fstab look like?--You could look at it & "see" what your device is--/dev/scd0 or someting like that--next, in a terminal---sudo mount /dev/scd0 (or whatever it is) & see what the response is-- The other choice is to mount it by "name"--let's say you named it "USB1"--that would then be sudo mount /dev/USB1--anyway--take a look & post back your info----

---

### Post by filemanager on 2005-08-03
[QUOTE=autocrosser]What 's your /etc/fstab look like?--You could look at it & "see" what your device is--/dev/scd0 or someting like that--next, in a terminal---sudo mount /dev/scd0 (or whatever it is) & see what the response is-- The other choice is to mount it by "name"--let's say you named it "USB1"--that would then be sudo mount /dev/USB1--anyway--take a look & post back your info----[/QUOTE]
 Right now it looks like this:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /boot           ext2    defaults        0       2
/dev/hda1       /mnt/win/c      vfat    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



---

### Post by cwaldbieser on 2005-08-04
This forum link might help:
[http://www.ubuntuforums.org/showthread.php?t=53728](http://www.ubuntuforums.org/showthread.php?t=53728) 

The problem in this case turned out to be the HAL, but I included notes on how you can manually figure out what device to mount, etc.

---

### Post by autocrosser on 2005-08-04
I think that cwaldbieser has the answer for you---looked at the threads & it fits your problems--

just for grins, I'm posting my fstab--could have ideas for you :-) 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc               /proc                 proc    defaults        0       0
/dev/hda7       /                       ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none                swap    sw              0       0
/dev/hda4      /home                ext3    defaults        1       2
/dev/hda5      /opt                   ext3    defaults        1       2
/dev/hda3      /tmp                   ext3    defaults        1       2
/dev/hda9      /mnt/osx             hfsplus defaults        0       0
/dev/hdb2      /mnt/osx3           hfsplus defaults        0       0
/dev/hdb3      /mnt/games        hfsplus defaults        0       0
/dev/hdb4      /mnt/storage      hfsplus defaults        0       0
/dev/hdc3      /mnt/itunes         hfsplus defaults        0       0
/dev/hdd2      /mnt/downloads  hfsplus defaults        0       0
/dev/hde        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdf         /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/scd0      /media/cdrom2    udf,iso9660 ro,user,noauto  0       0
/dev/sda        /media/usb0        auto    rw,user,noauto  0       0

I know it's for a mac, but take a look at /dev/scd0 & /dev/sda--scd0 is a external firewire CDRW & sda is a Dazzle card reader

---


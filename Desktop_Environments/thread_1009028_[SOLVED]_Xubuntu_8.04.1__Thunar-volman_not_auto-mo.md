---
title: "[SOLVED] Xubuntu 8.04.1 / Thunar-volman not auto-mounting correctly"
date: 2008-12-12
forum: Desktop Environments
---

### Post by ugm6hr on 2008-12-12
I installed Xubuntu 8.04.1 (32-bit) with a fresh install using the LiveCD over a previous 7.10 installation.

Everything went fine, and it works great.

Except one thing.  USB drives don't mount properly.

I can mount them from Terminal with the mount / umount commands.

However, plugging them in delivers the following error message (presumably as Thunar tries to auto-mount them):

> **Failed to mount "1G Removable Volume"**

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so.

I have no idea why.  The USB stick works fine on other computers.  And as I said, it mounts manually too.

What's going on?

---

### Post by Azyl on 2008-12-12
you should check your fstab file
use sudo gedit /etc/fstab

and see what it say at the line where your sdb1 dev is.

it should be something like /dev/sdb1 /media/usb auto user,noauto,exec 0 0

your mount point may vary "/media/usb"

you shoul check this [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Jose Catre-Vandis on 2008-12-12
If you still have problems, you might want to try installing hal
```
sudo apt-get install hal
```

This helped me with device recognition in Xubuntu and minimal installs in the past

---

### Post by ugm6hr on 2008-12-12
My fstab seem to be the problem.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6ec2a0d6-4e29-4b29-89a7-6e92f561e0e4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=49aeafbe-70d8-4986-9339-59b1116714a3 /home           ext3    relatime        0       2
# /dev/sda6
UUID=4f83689c-8950-4e2b-bd08-7be67811e33b none            swap    sw              0       0
**/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0**
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

For some reason, it seems to think /dev/sdb1 is an iso9660 format.

I'll experiment a little to try and sort it out.

---

### Post by ugm6hr on 2008-12-12
Commenting out the following line solved the problem:
```
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Not sure how that line got added in the first place!  From a fresh reinstall too.  Presumably something untoward happened the first time I plugged it in.

EDIT: I realise the problem is that I installed from a LiveUSB (rather than CD).  This obviously confuses the OS into mounting a USB stick as CD-ROM.  Hence the problem.  Easily solved if you know what's going on!

---


---
title: "Digital Camera support dead HELP!"
date: 2006-03-24
forum: Desktop Environments
---

### Post by radioraheem on 2006-03-24
I use Gnome almost exclusively for my digital cameras and for some reason the auto-mount/import apps have stopped working.

I really hate to say this but I may be forced to go back to dual booting, though I'd hate to reinstall Windows just for digital camera support.

Somebody please help!

---

### Post by taurus on 2006-03-24
Open a terminal and see what device (/dev/sda, /dev/sda1, /dev/sdb, etc.) the sytem thinks it is.  
```

dmesg | tail

```
Assuming that it is /dev/sda, then do
```

sudo mkdir /media/camera
mount -t vfat /dev/sda /media/camera

```
And if you want to unplug/remove the camera from your computer, do this first...
```

sudo umount /media/camera

```

---

### Post by radioraheem on 2006-03-24
Hmmm... I have a feeling I'm almost there.  Here's the output after I tried your suggestion.

> [ 8199.106249] sda: assuming drive cache: write through
[ 8199.133172] SCSI device sda: 32000 512-byte hdwr sectors (16 MB)
[ 8199.136062] sda: Write Protect is off
[ 8199.136071] sda: Mode Sense: 00 06 00 00
[ 8199.136077] sda: assuming drive cache: write through
[ 8199.136086]  /dev/scsi/host1/bus0/target0/lun0: p1
[ 8199.162977] Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
[ 8199.178235] usb-storage: device scan complete
[ 8314.972746] FAT: bogus number of FAT structure
[ 8314.972853] VFS: Can't find a valid FAT filesystem on dev sda.


any ideas?

---

### Post by taurus on 2006-03-24
Try
```

sudo mkdir /media/camera (if you haven't already done so...)
sudo mount /dev/sda /media/camera
-or-
sudo mount -t auto /dev/sda /media/camera

```

---

### Post by radioraheem on 2006-03-24
Tried both and got this each time:

mount: you must specify the filesystem type

---

### Post by taurus on 2006-03-24
Let's see your /etc/fstab then!!!
```

more /etc/fstab

```

---

### Post by radioraheem on 2006-03-24
```
jay@optimus:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---


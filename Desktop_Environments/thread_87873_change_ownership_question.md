---
title: "change ownership question"
date: 2005-11-09
forum: Desktop Environments
---

### Post by mwolfe on 2005-11-09
Alright i know most the basics of linux/unix systems, but for some reason i can't seem to figure this one out.. First, here is the contents of my fstab
```

mwolfe@wolfedell:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /media/hdc1     ntfs    defaults        0       0
/dev/hdc6       /media/hdc6     ntfs    defaults        0       0
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda2       /media/sda2     ntfs    defaults        0       0
/dev/sda4       /media/sda4     vfat    defaults        0       0
/dev/sda5       /media/sda5     ntfs    defaults        0       0
/dev/sda6       /media/sda6     vfat    defaults        0       0
/dev/sda7       /media/sda7     vfat    defaults        0       0
/dev/sda8       /media/sda8     vfat    defaults        0       0
/dev/hdc7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sdb        /media/usb0     auto    rw,user,noauto  0       0

```

now, my /dev/sda8 drive is fat32 as you can see, and i can read/write from this drive as root.. but i cannot change the ownership.. i always get a
an operation not permitted error even though i'm root.. And like i said, the disk is writeable as root.. Any ideas what the problem is? This computer is new and the hard drive setup is a bit funky i'll admit (ide drive and sata drive).. but i'm not sure whats going on with this.

 atdhvanknsce

---

### Post by ngms27 on 2005-11-09
There is no ownership attribute on FAT32!!!

Therefore you cannot set one!

JonnyT

---

### Post by adwait on 2005-11-09
Get your UID with this:
```
echo $UID
```
Now add this after the word "default"
> uid = <UID no you got>
eg:
> /dev/sda8       /media/sda8     vfat    defaults  UID=1000    0       0

---

### Post by mwolfe on 2005-11-09
how come i can't just change the umask to 0000 on the drive? thats what i'm pretty sure i had to do before now that i think back to my old system.

here is what i changed the line to
 /dev/sda8       /media/sda8     vfat    defaults,umask=0000        0       0

and then i did a mount -a 
and i still can't write to it.. wh

reading the tutorial 
[http://electron.mit.edu/~gsteele/linuxfaq/](http://electron.mit.edu/~gsteele/linuxfaq/)
that is what they said to do.. I'll try and do the uid thing next i'm just curious why that doesnt work.

---

### Post by mwolfe on 2005-11-09
alright i finally got it figured out.. i think the problem was just that i needed to close everything that was using the drive, unmount it, and then remount it.. doing mount -a didnt do anything until after i unmounted the drive, and in order to unmount a drive it can't be in use.

---


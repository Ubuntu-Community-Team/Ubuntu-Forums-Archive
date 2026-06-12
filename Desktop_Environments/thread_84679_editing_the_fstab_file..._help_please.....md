---
title: "editing the fstab file... help please...."
date: 2005-10-31
forum: Desktop Environments
---

### Post by recklessray on 2005-10-31
hi there, 

im a newb, thought id get that doen with! just a quick line about the fstab. i want my breezy system to mount my new hard drive automatically when i boot the pc. my new hard drive is hdc1. i usually mount it by typing the  following in BASH: mount /dev/hdc1 /mnt/160

here is a copy of fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


im just not sure about the systax - how to i make an entry to mount hdc1 on /mnt/160?

any help most appreciated :D

Ray.

---

### Post by aysiu on 2005-10-31
What filesystem is it? FAT32? NTFS? EXT3? Unknown?

---

### Post by super on 2005-10-31
you ned to know what the filesystem type is, but here is a general idea:

# <file system> <mount point> <type> <options> <dump> <pass>
     /dev/hdc1     /mnt/160?       xxxx     defaults    0          0

again, this is just an idea,

-the **filesystem** is where the device is located, aka the block device special file name

-the **mount point** is where you want to access the device aka the root of the mounted file system

-the **type** is the kind of filesystem that is formatted on the device, you can use auto here if you don't know the filesystem type

-the **options** are a list of option keywords for the device

-the **dump** number is for backing up the device. dump checks the system and uses the number to decide if a filesystem should be backed up. if it's zero, dump will ignore that filesystem.

-the **pass** number decides if the device will be checked or not

---

### Post by recklessray on 2005-11-01
hi, thanks, yes - sorry; its ext2.

---

### Post by SilentCacophony on 2005-11-01
Hi. It's easy to add that to /etc/fstab. I'd suggest mounting it in /media, though, as it would probably work better with gnome. For example, ubuntu would have set it up as /media/hdc1. If you wanted to do that, then:

make the directory:

```
sudo mkdir /media/hdc1
```

then add this line to /etc/fstab:

```
/dev/hdc1       /media/hdc1     ext2    defaults        0       2
```

then you can mount it from the fstab entry by:

```
sudo mount -a
```

---

### Post by recklessray on 2005-11-02
thanks for that - ill do that tonight. much apreciated :D

---

### Post by SickTwist on 2005-11-02
Incidentally, unless you have a lot of data on the disk already or a specific reason for using EXT2, there are much more robust filesystems you could use (EXT3 or Reiser are good choices) for the external HDD. EXT2 is not a journaling filesystem so there is a greater chance for data corruption if the disk looses power while operating.

---


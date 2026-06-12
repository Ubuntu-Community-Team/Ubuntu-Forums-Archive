---
title: "How do you mount a second FAT drive upon startup"
date: 2007-09-29
forum: Desktop Environments
---

### Post by sjoseph on 2007-09-29
I have three hard drives on my system. One with Windows, one with Ubuntu and a third large data drive set up to access through both OS's. What I'd like to do is have the data drive atomatically mount when I start up Ubuntu, rather than having to click on it and input my password to access it each time.

---

### Post by sjoseph on 2007-09-29
By the way, here is my fstab. i'd like to mount sdc5, is there a simple command to add.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=0f05e4fd-e750-40ae-bba3-dc8d7b9b53e8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb6
UUID=1d4f3cd3-6757-4d45-88b5-d2e4d2980350 /home           ext3    defaults        0       2
# /dev/sda1
UUID=8C4E-3E1E  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sdc5
UUID=EEB76C500064323F /media/sdc5     vfat    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/sdb5
UUID=940552e4-73af-4788-aa36-cae4f40fb47e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by sjoseph on 2007-09-30
can no one help me. please......

---

### Post by vanadium on 2007-09-30
Indeed, you need to add the drive to /etc/fstab in order to have it mounted at boot time.

---

### Post by sjoseph on 2007-09-30
it's already in fstab, but doesn't automatically mount, am i missing a command

---

### Post by logos34 on 2007-09-30
Post your fdisk

**sudo fdisk -l** (lowercase L)

Is there a mountpoint 'sdc5' in /media?

IS the uuid correct?

**blkid**

---

### Post by sjoseph on 2007-09-30
here's the fdsk:

Disk /dev/sda: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2494    20033023+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1824    14651248+  83  Linux
/dev/sdb2            1825        9729    63496912+   5  Extended
/dev/sdb5            9542        9729     1510078+  82  Linux swap / Solaris
/dev/sdb6            1825        9541    61986739+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
4 heads, 17 sectors/track, 5745911 cylinders
Units = cylinders of 68 * 512 = 34816 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           2     5745911   195360940    f  W95 Ext'd (LBA)
/dev/sdc5               2     5745911   195360931+   b  W95 FAT32

---

### Post by sjoseph on 2007-09-30
in the directory under system monitor, it shows the mount point for sdc5 as "media/disk"

---

### Post by sjoseph on 2007-09-30
how do i find out if the UUID is correct. it seems very different than the others.

---

### Post by logos34 on 2007-10-01
> how do i find out if the UUID is correct
[B]
blkid /dev/sdc5[/B]

or 
[B]
ls -l /dev/disk/by-uuid[/B]

> # /dev/sda1
UUID=8C4E-3E1E /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/sdc5
UUID=EEB76C500064323F /media/sdc5 vfat defaults,[COLOR="Red"]nls=[/COLOR]utf8,umask=007,gid=46 0 0

If sda1 is mounting ok, I wonder if the 'nls' is possibly causing a problem...take it out, make it match sda entry

Or try it without UUID:

> /dev/sdc5 /media/sdc5 vfat defaults,utf8,umask=007,gid=46 0 0

or 

> /dev/sdc5 /media/sdc5 vfat defaults,umask=0000 0 0

---

### Post by sjoseph on 2007-10-01
Thanks so much, it appears that the UUID was wrong, so I changed it to this in fstab and it mounts upon startup. Don't know where the other UUID came from.

/dev/sdc5: UUID=9731-6BB5

---

### Post by sjoseph on 2007-10-04
turns out the UUID was incorrect in fstab, changed it and the drive mounts correctly upon startup. thanks for all the help. how is it that the UUID was wrong i wonder...

---


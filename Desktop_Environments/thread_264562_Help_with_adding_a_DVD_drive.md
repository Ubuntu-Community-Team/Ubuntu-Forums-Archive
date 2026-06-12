---
title: "Help with adding a DVD drive"
date: 2006-09-24
forum: Desktop Environments
---

### Post by Desabrir on 2006-09-24
I installed the amd64 version of Dapper and forgot I had my DVD drive disconnected from my system.

How do I add it to my system to make it work like my CD-RW drive that was there when Dapper installed itself. 

I've searched the forums and the web for just a guide to permanently add a second drive, but only seem to find pages that deal with problems with people's already installed second drive or whatnot.

The DVD drive is installed as a slave drive to the CD-RW which is the master on the secondary IDE

here is my fstab that i've been playing with in order to get it to work:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1    ext2    defaults,	0       0
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb2       /media/sdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0


The /media/cdrom1 is the second drive i'm trying to get up and running.

Some help would be appreciated.

h4n5

---

### Post by reclusivemonkey on 2006-09-25
> **Desabrir said:**
> I installed the amd64 version of Dapper and forgot I had my DVD drive disconnected from my system.

How do I add it to my system to make it work like my CD-RW drive that was there when Dapper installed itself. 

I've searched the forums and the web for just a guide to permanently add a second drive, but only seem to find pages that deal with problems with people's already installed second drive or whatnot.

The DVD drive is installed as a slave drive to the CD-RW which is the master on the secondary IDE

here is my fstab that i've been playing with in order to get it to work:



The /media/cdrom1 is the second drive i'm trying to get up and running.

Some help would be appreciated.

h4n5

Erm, remove the "#" for starters (that signifies a comment line to be ignored by your computer) then make 

```

/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0

```

read

```

/dev/hdd /media/dvd iso9660 user,noauto 0 0

```

You can't have /dev/hdc twice! The /media/dvd won't make a difference to it working, its just a better name. Not sure whether you need udf, I am not sure what that is.

---

### Post by Desabrir on 2006-09-25
Thanks, I'll try it out later after work.

That line was commented out while I was trying to figure out the correct configuration.

h4n5

---


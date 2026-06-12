---
title: "NTFS Partitions"
date: 2008-07-19
forum: Desktop Environments
---

### Post by newtwoubun2 on 2008-07-19
My NTFS Partition cannot be seen. I originally set it up but the system lost power ungracefully and ever since it cannot see my NTFS partition?

I have tried to modify the /etc/Fstab file but I guess I do not know enough on just what and how to enter the info.

It is listed on the desktop as Drive1 and I think it is known to the system as hdb1 where hdba is my (master) drive with Ext3 partition

any help is appreciated.

WM:guitar:

---

### Post by newtwoubun2 on 2008-07-19
Ok I see that I made an error in my post. the EXT3 drive I think is hda1 not hdba. oops!

Also here is a screen capture using gksudo gedit /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=2cce8d44-7445-420e-925b-030a453771d6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1a0a7d7c-d615-4ceb-a290-8761d34fc6a2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by coffeecat on 2008-07-19
NTFS is a journalling filesystem and because it was shut down uncleanly, it may need repair. I'm posting from my Mac atm, so I can only give you a lead. If I was in ubuntu I could give you the exact commands to use. :)

Check out the ntfsprogs suite of programs. I think they come with a default install. There's about half-a-dozen utilities and one of them (can't remember the name but it begins with ntfs) can repair NTFS filesystems. Open a terminal and type ntfs and then press the tab key twice and it will give you a list of all the command utilities beginning with ntfs. Find the one that looks like the one I am struggling to explain ( :wink: ) and do 'man whateveritscalled' and that should tell you what you can do.

---

### Post by sisco311 on 2008-07-19
Are you dual booting?
post:
```
sudo fdisk -l
```

---

### Post by coffeecat on 2008-07-19
**newtwoubun2**, I'm in Ubuntu now and I may have slightly misled you. The utility I was trying to remember was ntfsfix. From the man page:

> NAME
       ntfsfix - fix common errors and force Windows to check NTFS

SYNOPSIS
       ntfsfix [options] device

DESCRIPTION
       ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

       You may run ntfsfix on an NTFS volume if you think it  was  damaged  by
       Windows or some other way and it cannot be mounted.
It may do the trick by itself, but it sounds as though it might need Windows to complete the job. Do you have Windows on that machine?

---


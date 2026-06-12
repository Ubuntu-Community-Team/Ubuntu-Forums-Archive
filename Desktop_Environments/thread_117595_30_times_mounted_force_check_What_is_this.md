---
title: "30 times mounted? force check? What is this?"
date: 2006-01-15
forum: Desktop Environments
---

### Post by kenweill on 2006-01-15
When I started my computer now, it produces a message with something like:
Checking root partition
"it has been mounted 30 times and it has not been checked. Force check"

What that does mean? What did it check?

---

### Post by Gowator on 2006-01-15
[QUOTE=kenweill]When I started my computer now, it produces a message with something like:
Checking root partition
"it has been mounted 30 times and it has not been checked. Force check"

What that does mean? What did it check?[/QUOTE]


Its no problem its like the old windows scandisk thing...

If you look in /etc/fstab you will see the / partition has the number 30 at the end of the line...
All it does is do a file system integrity check every 30 mounts to prevent cumulative errors.  You can increase the number but its just a health test every so often and best left in :D

---

### Post by kenweill on 2006-01-15
[QUOTE=Gowator]Its no problem its like the old windows scandisk thing...

If you look in /etc/fstab you will see the / partition has the number 30 at the end of the line...
All it does is do a file system integrity check every 30 mounts to prevent cumulative errors.  You can increase the number but its just a health test every so often and best left in :D[/QUOTE]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

There's no 30 at the end. I wonder.
If its like scandisk, how can I check it manually?

---

### Post by Gowator on 2006-01-15
[QUOTE=kenweill]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

There's no 30 at the end. I wonder.
If its like scandisk, how can I check it manually?[/QUOTE]


You use fsck but you should unmount or have it read only before correcting any errors and the easiest way to do this is actually at boot up ... which is the remount -ro .. I guess 30 is defaults ?  

Its nothing to panick about though 

try 
man fsck

---

### Post by stoffe on 2006-01-15
You can use tune2fs to change this behavior, try "man tune2fs" for more details. As it says there, it may not advisable to turn checking off completely, but you can do it - or you can increase the interval between checks.

---

### Post by rado_london on 2006-01-16
I hate this function. I know that is useful but all the time my dad uses my laptop he waits for ages to load. He always gets that 30 time period of checking. Hes unlucky. I wonder what is going to happen if I disable that. If it is not important can you tell me exactly how to do that.

Cheers

---

### Post by CopaceticOpus on 2007-08-06
There really needs to be an option to abort the check and do it next time. On my system the check is very slow. I don't mind sometimes, but if I need to use my computer in a hurry it is a major pain.

---

### Post by AZzKikR on 2007-08-07
Can't you cancel that with ^C? I've never tried it, since I never needed to even try to abort it ...

---

### Post by ssam on 2007-08-07
[https://wiki.ubuntu.com/AutoFsckspec](https://wiki.ubuntu.com/AutoFsckspec) may be a good solution to disk checks at boot time.

> AutoFsck a script which automates periodic disk checking in such a way that it no longer bothers the user every 30 boots, and is streamlined in a friendly graphical user interface.

AutoFsck ensures that the automatic disk check will no longer inconvenience you by making your boot times very long. 

the author want it to be in ubuntu 7.10 gutsy


> **AZzKikR said:**
> Can't you cancel that with ^C? I've never tried it, since I never needed to even try to abort it ...

it is a very bad thing to stop fsck in the middle of a disk check. it could leave the disk in a corrupted state

---


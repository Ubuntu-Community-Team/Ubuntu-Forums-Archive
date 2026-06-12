---
title: "Repartitioning"
date: 2006-05-31
forum: Desktop Environments
---

### Post by InsanePenguin08 on 2006-05-31
Trying to repartition /dev/hda1 from the live CD, and it says it's unmounted, but when gparted tries to make changes it always says that there is at least one busy partition.  

The only other partitions I have are hda2 which is listed as an extended file system (it is busy even when I'm using the live CD) and hda5, which is in a drop-down menu of hda2.  hda5 is the swap memory and is active.  

I tired to manually unmount hda1, hda2, and hda5 in the Terminal, but it says that they're all unmounted.
```

sudo umount /dev/hda1
``` 

That's the command I used (changing hda1 to hda2 and hda5, of course)

Anyone able to help me see what I'm doing wrong?  I'd really appreciate it!  Thanks!

---

### Post by aysiu on 2006-05-31
For a good program, try [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142).

DiskDrake has never failed me, but it does entail downloading another distribution. GParted with and QTParted should theoretically also work... but, as you can see, that's not always the case.

---

### Post by az on 2006-05-31
[QUOTE=InsanePenguin08]hda5 is the swap memory and is active.  

![/QUOTE]


sudo swapoff -a

or just use the Dapper live (Desktop) cd.

---

### Post by InsanePenguin08 on 2006-05-31
Okay, that allowed it to be partitioned, but when it tried to format it into NTFS, I got an error, with these as possible reasons:
> Unable to detect filesystem! Possible reasons are:
-The filesystem is damaged
-The filesystem is unknown to libparted
-There is no filesystem available (unformatted)

Anyone able to tell me what I can do about that?

---


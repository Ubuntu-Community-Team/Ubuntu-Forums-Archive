---
title: "Thunderbird Problem"
date: 2006-05-30
forum: Desktop Environments
---

### Post by JNik on 2006-05-30
I am running Dapper on my laptop for a long time now. Since the last time I updated my system I get the following error when I try to open Thunderbird.

```

Could not initialize the browser's security component. The most likely cause is
problem with your browser's profile directory. Please check that this directory
has no read/write restrictions and your hard disk is not full or close to full. It 
is recommended that you exit the browser and fix the problem. If you 
continue to use this browser session, you might see incorrect browser 
behaviour when accessing security features.

```

Thunderbird then opens but I can't see the list of my e-mails or receive new ones.

When I close Thunderbird and I try to open it again, I get the following message:

```

Mozilla-Thunderbird is already running, but is not responding. To open a new
window, you must first close the existing Mozilla-Thunderbird process, or 
restart your system.

```

In the System Monitor there isn't any Thunderbird's proccess!!


I read [this]("http://forums.mozillazine.org/viewtopic.php?t=272556") and I deleted cert8.db and secmod.db, but still no luck.


Thunderbird's profile is in a fat partition
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,umask=000        0       0
/dev/hda2       /media/hda2     vfat    defaults,umask=000        0       0
/dev/hda5       /media/hda5     vfat    defaults,umask=000        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Any ideas?

---

### Post by JNik on 2006-06-03
I found what was wrong. Some of the files in my profile were corrupted :-(

I moved the ones I could in a new location and now every works ok again :-)

---


---
title: "External USB Drive keeps &quot;going away&quot;"
date: 2008-02-25
forum: Dell  Ubuntu Support
---

### Post by jadoti on 2008-02-25
I'm not sure if this is a dell issue or not, it's connected to a dell system, please move this thread if necessary...

I have an external Seagate USB drive that I leave plugged into my Dell 410n w/ Ubuntu 7.10.  I leave both powered on all the time, and the problem I'm having is that the USB drive (or should I say it's partitions) get quirky after a little while.

Essentially what happens, is I'll be working, and when I go to access one of the partitions on the USB drive, it will give me some weird error, either I can't access the partition, or it will show me some folders of the partition and not let me do anything, or show some folders but they're not showing up as folders.

Anyways, I can fix the problem by unmounting the drive and remounting, then everything works.

There's no set time for it to start acting quirky, I thought it was because the drive or PC was inactive for a while but it will happen while I'm working on the box, in between times when I actually access the drive.

Anyone else have this problem, or an idea of how I can make it stop, so that the drive is more "permanent"?  As of now, I can never trust that the drive will be there when anything is running.

---

### Post by kgr132 on 2008-02-25
This sounds exactly like what I was experiencing. The external HDD is spinning down (aka sleeping) and Ubuntu can't wake it up. My solution was to disable that feature on my external HDD. See my previous post here:
[http://ubuntuforums.org/showthread.php?t=636783](http://ubuntuforums.org/showthread.php?t=636783)

---

### Post by jadoti on 2008-02-25
> **kgr132 said:**
>  See my previous post here:
[http://ubuntuforums.org/showthread.php?t=636783](http://ubuntuforums.org/showthread.php?t=636783)

Thanks much! I'll try it when I get home tonight and see if that works.

Mike

---


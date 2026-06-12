---
title: "Starting Firefox makes partition turn readonly?!"
date: 2009-04-19
forum: General Help
---

### Post by inanutshellus on 2009-04-19
I have a dual boot machine with a partition I use for info I want visible to both XP and Ubuntu, including my Firefox and Thunderbird profiles. 

Earlier this week we had a blackout and ever since my Firefox and Thunderbird have been acting crazy. It took me a while to figure out, but basically, the partition is totally OK and RW until I start firefox. Instead of actually starting though, I get a security error:


```

Could not initialize the application's security component. 
The most likely cause is problems with files in your application's 
profile directory. Please check that this directory has no read/write 
restrictions and your hard disk is not full or close to full. It is 
recommended that you exit the application and fix the problem. If you 
continue to use this session, you might see incorrect application 
behaviour when accessing security features.

```

If I close that dialog and reopen Firefox I get this error:

```

Firefox is already running, but is not responding. To open a new 
window, you must first close the existing Firefox process, or 
restart your system.

```

At this point, if I go check the partition it has switched to read only! and I can't unmount it or mount it. 

```

$ umount /media/fileshare/
/sbin/umount.hal: Unmounting /media/fileshare failed: 
org.freedesktop.Hal.Device.Volume.NotMountedByHal: 
Device to unmount is not in /media/.hal-mtab so it is not 
mounted by HAL

```

```

$ mount /media/fileshare/
mount: according to mtab, /dev/sda2 is already mounted on /media/fileshare
mount failed

```

I have to reboot in order to get things back to right.

Removing my  ~/.mozilla folder (the one that redirects firefox to my shared partition profile) fixes the issue, but (a) I lose all my settings of course and (b) I can't use my shared profile anymore and (c) I'd prefer to know what the hell is actually going on here. 

Any ideas?

---

### Post by inanutshellus on 2009-04-20
Asking a question on a weekend = fail...

It appears I'm not the only person that's ever had this problem though, as seen here:

[http://ubuntuforums.org/archive/index.php/t-889272.html](http://ubuntuforums.org/archive/index.php/t-889272.html)

Though that guy never "solved" it either.

---

### Post by msb@ichp.ufl.edu on 2009-04-26
i ran across your post searching for answers to a sort of similar problem, my ubuntu box has been running fine for about 1 yr then all of a sudden last week it started acting up, the disk  keeps getting marked read only and i cant figure out why...

---


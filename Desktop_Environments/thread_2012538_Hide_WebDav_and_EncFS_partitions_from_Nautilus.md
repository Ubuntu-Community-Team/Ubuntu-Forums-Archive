---
title: "Hide WebDav and EncFS partitions from Nautilus"
date: 2012-06-29
forum: Desktop Environments
---

### Post by zedixal on 2012-06-29
Hi,

I have set up in my box a WebDAV partition (and a related EncFS partition); they work fine, but they show up in the left pane of Nautilus as they were removable drives.

Is there any way to hide them from Nautilus? I'm getting tired of clicking by accident the eject button!

I'm aware of this thread: 

[http://ubuntuforums.org/showthread.php?t=1439003](http://ubuntuforums.org/showthread.php?t=1439003)

and this solution: 

[http://www.worldofnubcraft.com/969/hide-your-disks-or-partitions-from-nautilus/](http://www.worldofnubcraft.com/969/hide-your-disks-or-partitions-from-nautilus/)

but my case seems different, since I can't (e.g. I'm not able to) find a "name" or UUID for my WebDAV/EncFS partitions.


TYIA

---

### Post by zedixal on 2012-07-01
A bump

](*,)

---

### Post by zedixal on 2012-07-07
Auto-generated solution of the question!

After some research :p I can say that Nautilus left pane ignores all devices mounted elsewhere than:

/media
/home

The second was my case; so I simply mounted my WebDAV and EncFS partitions in /mnt. 

Marked as SOLVED

---


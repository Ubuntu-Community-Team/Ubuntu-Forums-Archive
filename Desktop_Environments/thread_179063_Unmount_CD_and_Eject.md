---
title: "Unmount CD and Eject"
date: 2006-05-18
forum: Desktop Environments
---

### Post by qyot27 on 2006-05-18
This is for my Fluxbox menu.  I'd like to be able to unmount a CD and then eject using only one menu command (for instance, Right-click->Removable Media->Unmount CD & Eject).  How - if this is even possible - could I do that?  As it stands right now I can do either from the menu but I'd like the process streamlined.  Inputting multiple commands on one line isn't what the ; separated terminal operations are, are they?  I'm really only familiar with a few terminal commands at this point, so I'm just guessing there.

As an aside, how exactly are the disc drives assigned to mount points in cases where the system is set to automount them?  I seem to have experienced that whichever drive gets something inserted into it automatically gets the /media/cdrom/ and /media/cdrom0/ directories associated to it, but maybe it's just the master drive and I'm hallucinating.  I have a CD-R/W drive and a DVD±R/W drive with the DVD drive as the master.  Does the DVD drive always get /media/cdrom/ and /media/cdrom0/ or does it switch back and forth depending on which actually has a disc in it at the time (or at least, which had a disc in it first)?  If it does switch around, is it possible to make it static so that the thread topic's menu commands can be used uniformly for one drive or the other?

Thanks in advance.

---

### Post by bluevoodoo1 on 2006-05-19
something like...

```
umount /dev/cdrom && eject
```

works for me. I only have one disc drive, so there's more to mess around with if you have 2. (So I'm not sure!)

---

### Post by Psquared on 2007-02-27
> **bluevoodoo1 said:**
> something like...

```
umount /dev/cdrom && eject
```

works for me. I only have one disc drive, so there's more to mess around with if you have 2. (So I'm not sure!)

wouldn't that be "umount /dev/hdc && eject" ???

---


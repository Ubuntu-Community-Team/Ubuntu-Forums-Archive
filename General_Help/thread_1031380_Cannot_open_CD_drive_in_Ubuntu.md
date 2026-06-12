---
title: "Cannot open CD drive in Ubuntu"
date: 2009-01-05
forum: General Help
---

### Post by joey-elijah on 2009-01-05
This is becoming a recurring annoyance during most of my installs. Ican eject the tray and pop a CD in, but if i then want to eject it i'm not allowed.

the "old" fix used to be close firefox and it'd then let me (no idea why?!) but now that doesn't work. Pressing the eject button on the drive doesn't get me anywhere either.

The 'complaint' is that I'm apparently not "privileged" enough to eject a CD. Which is a bit of an over sight? Because even a guest user should have the ability to use CD's etc. (And not be stuck with one.)

Any ideas?

---

### Post by editrix on 2009-01-07
Try this:

```
sudo fuser -k /media/cdrom0
``` or whatever your drive is called. Then type:

```
eject
```

There's a gazillion bugs related to CD drives/burning on launchpad, this may be one of them.

---


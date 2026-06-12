---
title: "ALERT! /dev/hda4 does not exist! Dropping to a shell."
date: 2006-07-09
forum: Desktop Environments
---

### Post by frbhg on 2006-07-09
I know this subject has been hammered at, but let's try it again, because right now I'm running on the LiveCD and while I can get my email and use the web this way, it's kinda like living in a motel room.

This is most definitely NOT a problem of Dapper renaming my devices to something else. My boot drive was hda4 before the upgrade and that's where I find it now while running Dapper from the LiveCD.

My setup:
80GB HD on IDE0
CD-RW on IDE1
no SATA drives

As vanilla as it gets.

One thing I noticed: the /dev directory on my upgraded HD has almost no device files: only 117. By contrast, the /dev directory on the LiveCD has 754 files. It would seem that my installed Dapper has trouble with more than just hdaX devices.

---

### Post by taurus on 2006-07-09
Open a terminal (Applications -> Accessories -> Terminal) and type in this command.  Paste the out here...
```

sudo fdisk -l 

```

---


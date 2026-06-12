---
title: "cannot change permissions on ipod"
date: 2005-10-18
forum: Desktop Environments
---

### Post by kdavison007 on 2005-10-18
So I had my iPod (4th gen 20gig) working fine and then one day GTKPOD reported that my file system was read only.  I quickly checked and confirmed that the ipod_control directory was owned by "99" and grp "99" instead of kevin and kevin.  The mount point was fine and when I try to sudo chown or sudo chmod /media/ipod I just get an error that states "file system is mounted read-only"  I'm on Breezy Badger with gtkpod .94 i believe.  

Any ideas?   I've had nothing but problems with this!

---

### Post by Aurels on 2005-10-19
In the /etc/fstab file (where ou specify mount points):

you can set an option uid (which uid is owner of the mounted tree). For exemple:

```
/dev/sdX    /media/ipod     hpfs     defaults,uid=1000     0     0
```

---


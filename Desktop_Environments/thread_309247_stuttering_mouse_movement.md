---
title: "stuttering mouse movement"
date: 2006-11-29
forum: Desktop Environments
---

### Post by rsv869 on 2006-11-29
A few days ago I installed ubuntu 6.10. It's working well, but I've noticed that the mouse pointer (regardless of which kind of device I use: optical or the old ball type) doesn't move smoothly. I've tried adjusting the settings in Prefrences, but see no change. My hardware is: AMD x86_64, Asus MB.

Ever seen this before? An suggestions about where to check for info?

Thanks

Reid

---

### Post by mgmiller on 2006-11-29
The closest I ever came to that was having my mouse cursor start flickering.  This was with nvidia drivers.  I added the following line to the /etc/X11/xorg.conf file in the nvidia device section:
```
Option 		"HWCursor" "off"
```

You would need to restart x to see any changes.

---


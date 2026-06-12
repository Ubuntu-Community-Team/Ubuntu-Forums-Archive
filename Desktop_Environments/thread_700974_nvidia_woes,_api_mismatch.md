---
title: "nvidia woes, api mismatch"
date: 2008-02-18
forum: Desktop Environments
---

### Post by cokehabit on 2008-02-18
Ok, this is a weird one...

After not being able to get the desktop effects for a while I decided to something about it today so i installed Xorg-xgl and enabled the proprietary nvidia drivers but the only effect that had was to make it completely ignore the drivers and it seems to be using the backup mesa driver instead (I only have 800x600 and the mouse barely works).

Anyway, I removed it from the restricted drivers manager, and installed the -new nvidia driver and the glx one.

When I have a look in dmesg it tells me ```
[  123.736331] NVRM: API mismatch: the client has the version 169.09, but
[  123.736335] NVRM: this kernel module has the version 169.07.  Please
[  123.736338] NVRM: make sure that this kernel module and all NVIDIA driver
[  123.736341] NVRM: components have the same version.
```I am unsure of what has happened there...

Any ideas?

---


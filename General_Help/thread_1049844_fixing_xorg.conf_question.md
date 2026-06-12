---
title: "fixing xorg.conf question"
date: 2009-01-25
forum: General Help
---

### Post by Inane_Asylum on 2009-01-25
I rebooted my computer, and it booted into command line.  Trying startx showed ```
fatal error: no screens found
```
along with something like ```
VESA(0): no valid modes
```
So I figured my xorg.conf got gorked somehow ](*,).  What I ended up doing is booting a livecd (same distro), making a backup of my original xorg.conf, going into the livecd's /etc/X11/ and typing ```
 sudo cp /etc/X11/xorg.conf /media/disk/etc/X11/xorg.conf 
```
After rebooting, it seems to be working fine.  I'm just wondering if that's a suitable fix or not...

---


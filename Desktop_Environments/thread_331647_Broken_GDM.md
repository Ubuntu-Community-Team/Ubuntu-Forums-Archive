---
title: "Broken GDM"
date: 2007-01-04
forum: Desktop Environments
---

### Post by tari on 2007-01-04
I just setup a Xubuntu machine by installing a minimal system from my Edgy Alternate CD, then installing xubuntu-desktop.  My problem is, I get a blank screen when GDM starts.  I get the Xubuntu splash screen as it's starting, but GDM gives a black screen, even when started from the recovery console.
Does anyone know what's going on?  I haven't installed any display drivers or the like, and I don't have a clue.

---

### Post by pay on 2007-01-04
Try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```If that doesn't work can you post your xorg.conf?```
cat /etc/X11/xorg.conf
```

---


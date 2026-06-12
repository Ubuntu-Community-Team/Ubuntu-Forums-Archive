---
title: "xpad - no i don't mean the note thingy"
date: 2005-04-29
forum: Gaming &amp; Leisure
---

### Post by seasidebaz on 2005-04-29
I'm trying to install my xbox pad on hoary, got the xpad drivers from the xbox-scene site but can't install. has anyone else tried this? the pad appears correctly (as a usb hub with a pad attached) but no drivers! if anyone has got this to work please let me know

---

### Post by dude2425 on 2005-04-29
Try doing a quick `sudo echo xpad >> /etc/modules` and `sudo modprobe xpad`
That should make sure the driver gets loaded, and keeps loading when you reboot.
IIRC, the Linux Kernel already has xpad in it, so there's no need to install it yourself.

---

### Post by seasidebaz on 2005-05-01
marvelous ta very much :D

---


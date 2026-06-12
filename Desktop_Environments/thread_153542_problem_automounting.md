---
title: "problem automounting"
date: 2006-04-01
forum: Desktop Environments
---

### Post by Requiem on 2006-04-01
I dunno what I did but my usb drive doesn't automount in ubuntu, it does in windows...

gnome-volume-manager is running
automounting is cheked in gnome-volume-preferences
sda1 isn't mentioned in fstab...
pmount /dev/dsda1 works
I have rebooted several times


Any ideas?

---

### Post by stevea1210 on 2006-04-01
type  "mount" at a terminal to ensure it isn't being mouted somewhere other that where you are expecting.  Mount will show everything that is currently mounted.


I remember there being a bug a month or two ago with this.  It was resolved with an update.  Make sure you have your system up to date.

---


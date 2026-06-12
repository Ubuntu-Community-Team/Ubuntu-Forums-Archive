---
title: "non-removable drive -- icon on desktop"
date: 2009-03-14
forum: General Help
---

### Post by emwine on 2009-03-14
After upgrading 7.10 --> 8.04 --> 8.10, an icon for an internal drive appeared on my desktop, and it's annoying.  The drive is mounted under my home directory from fstab -- I use it as temporary space for video editing.  How come it's on my desktop at all when it's non-removable, and how do I get rid of it without unmounting it?

I know how to tell gnome not to show removable icons on the desktop.  I still want that behavior for thumb drives and other removable devices.

---

### Post by zvacet on 2009-03-15
In terminal

```
gconf-editor
```

**apps<nautilus>desktop** and on the right side uncheck **volumes_visible**.

---

### Post by heindsight on 2009-03-15
Apart from removable drives, any filesystems mounted under your home directory will also be shown on your desktop if you have apps/nautilus/desktop/volumes_visible enabled in gconf.

Try mounting it somewhere else, perhaps somewhere under /mnt or /media and then replace the mountpoint in your home directory with a symbolic link to the new mountpoint.

---

### Post by emwine on 2009-03-15
> **heindsight said:**
> Try mounting it somewhere else, perhaps somewhere under /mnt or /media and then replace the mountpoint in your home directory with a symbolic link to the new mountpoint.

This is what I had to do.  Since I need write access to it, I had to chown and chgrp the new mountpoint to my regular user.

---


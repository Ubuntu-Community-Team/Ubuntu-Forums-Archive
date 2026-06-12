---
title: "Mounted drive doesn't appear in Places/Desktop"
date: 2007-09-29
forum: Desktop Environments
---

### Post by disposition on 2007-09-29
When I mount a drive to /media/distopia, it doesn't appear on Desktop/in Places. I can still access it by navigating to /media/distopia

The volumes_visible option in gconf is enabled.

This is the entry in my fstab:

```
/dev/sdb1	/media/distopia	ntfs-3g	defaults,auto,locale=en_US.utf8	0	0
```

I've exhausted most of the options... anyone have an idea? It used to mount just fine, and then stopped after a reboot one day.

---

### Post by disposition on 2007-09-29
Also, when I open gparted I get this:

```
======================
libparted : 1.7.1
automounting disabled
======================

```

How can I reenable automounting? Could this be conflicting with gnome's ability to mount the drive?

---


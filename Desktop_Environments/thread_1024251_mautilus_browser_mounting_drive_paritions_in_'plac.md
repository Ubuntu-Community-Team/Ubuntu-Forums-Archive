---
title: "mautilus browser mounting drive paritions in 'places' view"
date: 2008-12-28
forum: Desktop Environments
---

### Post by graysky on 2008-12-28
I have several ntfs partitons that I'd like to see as icons in my nautilus browser.  To mount them, I've been using the following:

```
$ sudo mount -t ntfs-3g /dev/sda1 ~/C
$ sudo mount -t ntfs-3g /dev/sda2 ~/D
```

I'd like to be able to mount the partitions though Gnome, but neither of them show up in my nautilus 'Places' view, nor on the desktop.  How does one configure a partition to appear in this view and as well on the desktop when mounted?  I found gconf-editor then apps>nautilus>desktop: volumes_visible (which is checked), but I suspect this only works when mounted through the GUI.

Thanks for the info!

---

### Post by taurus on 2008-12-28
Try using ntfs-config.  You want to mount them to /media/C & /media/D or something similar to those.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by graysky on 2009-01-02
Tried it, but it doesn't behave was I'm used to.

Under Debian/Lenny, an icon would appear on my desktop when I'd issue the command:
```
$ sudo mount -t ntfs-3g /dev/sda2 ~/D
```

I didn't mess with fuseblock at all.  I'd like to get this behavior with Ubunutu.

---


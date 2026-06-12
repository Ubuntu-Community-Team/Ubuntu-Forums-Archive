---
title: "Manually mount CD-ROM drive in Nautilus"
date: 2009-09-04
forum: Desktop Environments
---

### Post by Amurko on 2009-09-04
It seems in a previous installation of Ubuntu, the CD-ROM drive always showed up in Nautilus; if it didn't have a CD inside, it would show up as an icon of an ejected drive (with options to manually mount.)  Due to some hardware problems my drive suffered, it no longer can mount any CDs manually.  I can still access it the following way:

sudo mount /dev/sr0 /cdrom

and unmount:

sudo umount /cdrom

However, it's a bit inconvenient to have to run this in a terminal or click on scripts on the desktop every time I need to use the CD-ROM drive.

Btw, I go under System -> Preferences -> Removable Drives and Media

and there is no longer a tab for CD-ROMs..  it only has tabs for Cameras, PDAs, printers, etc.  I remember I used to go here to change settings for CDRoms

So is there any way I can get the CD-ROM drive to always show up in Nautilus and the GNOME disk mounter panel even when no CD is mount (so I can right click it to force it to try to mount the CD.)?

---


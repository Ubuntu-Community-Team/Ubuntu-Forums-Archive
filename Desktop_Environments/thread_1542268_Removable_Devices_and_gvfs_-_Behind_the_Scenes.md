---
title: "Removable Devices and gvfs - Behind the Scenes"
date: 2010-07-30
forum: Desktop Environments
---

### Post by lojack2374 on 2010-07-30
So, I've spent a great deal of time trying to determine what exactly
happens when a removable storage device is plugged into a machine running
stock Ubuntu 10.04 with Gnome 2.30. I (think I) understand that hal, udev
and gvfs all play a role in mounting the filesystem found on the device
thereby making it available to the user. But, what I can't figure out is
what exactly is going on in the background to make this work.

For example, if I add the Disk Mounter widget to the panel then plug a
USB flash drive into my machine after a moment an icon will appear on the
panel (thanks to Disk Mounter) and Nautilus will autostart at the root of
the flash drive's filesystem. The filesystem is automagically mounted for
me with read/write permissions -- even for NTFS filesystems. If I wanted
to tweak this process a bit, where would I begin?

I've been all through gconf and cannot find any settings related to gvfs
and udev. I am probably just looking in the wrong places. I've been
through the docs here [http://library.gnome.org/admin/deployment-guide/](http://library.gnome.org/admin/deployment-guide/)
and here [http://library.gnome.org/admin/system-admin-guide/2.30/](http://library.gnome.org/admin/system-admin-guide/2.30/). Still I
cannot find a guide describing this function. Do I add or alter a udev
policy? Is there a conf file for gvfs somewhere that I cannot find? Can
anyone point me in the right direction? Anyone aware of a good HOWTO for
tweaking gvfs and udev in Ubuntu 10.04?

Thank you.


--
Chris

---


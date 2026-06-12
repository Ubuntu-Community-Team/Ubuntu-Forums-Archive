---
title: "GNOME Placing Media on Quick Launch Bar"
date: 2007-12-16
forum: Desktop Environments
---

### Post by TreeFinger on 2007-12-16
I currently have 2 media devices (harddrives) on my desktop. I'd like to place them on the quick launch bar instead of having them on the desktop. I am having trouble figuring out how to do this. Is it possible?

Thanks in advance.

---

### Post by vanadium on 2007-12-16
All devices that are mounted in /media appear on the desktop. These include removable devices (USB sticks, drives) but also fixed disks. In gconfig-editor, tehre is an option to disable showing the icons on your desktop. This also prevents removable drives to appear on your desktop.

If you want fixed disks not to appear, but still want removable drives to appear, then the only option is to mount the fixed disks elsewhere than under /media. That is not very difficult: it involves moving the mount points from media to elsewhere (typically /mnt) and updating the /etc/fstab file. If you need detailed instructions on how to do this, post  your /ets/fstab here along with the output of "ls -l /mount"

---


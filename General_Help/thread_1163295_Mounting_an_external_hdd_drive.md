---
title: "Mounting an external hdd drive"
date: 2009-05-18
forum: General Help
---

### Post by hduguay on 2009-05-18
My external 500 gb drive is no longer mounted to my desktop. It shows to be mounted but no longer showing on the desktop. Any help with this would be greatly appreciated

---

### Post by HermanAB on 2009-05-18
Howdy, some debug tips:

To see what is mounted:
$ sudo mount

To see what is plugged in:
$ dmesg

To unmount a drive that doesn't want to unmount:
$ sudo -l /dev/sdXY

So, to get you drive mounted, replug it and check with dmesg to see what is going on.  Maybe mount it manually with:
$ sudo mkdir /mnt/disk
$ sudo mount /dev/sdXY /mnt/disk

Hope that helps!

---


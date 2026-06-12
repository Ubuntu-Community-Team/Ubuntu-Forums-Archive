---
title: "Solved: Cannot mount USB after install from live USB"
date: 2008-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rallg on 2008-10-21
My mini 9 came with XP (sorry, folks) and 16G storage. I used unetbootin to create a bootable USB of the live Ubuntu 8.10 beta, and installed Ubuntu to a new partition.

When I run Ubuntu from my installed partition, it was unable to mount my various USB sticks.

The problem was that during install, the live USB was detected and described within fstab as a "CDROM" mounted to /dev/sdb using its specific UUID. Later, when running the installed system, it would attempt to mount a USB to /dev/sdb but reject it because it had the wrong UUID (and it was not pretending to be a CDROM).

The solution was simple: Remove the offending line from fstab. Code:

gksudo gedit /etc/fstab

and if you see a reference to a CDROM mounted to /dev/sdb, comment out the line by putting # in front of it. Save, then reboot.

---

### Post by C.S.Cameron on 2008-10-21
I think this has been fixed in the latest 8.10 daily-fix.
Located here:
[http://cdimage.ubuntu.com/daily-live](http://cdimage.ubuntu.com/daily-live)

---

### Post by Rallg on 2008-10-22
Fixed in the daily build? Good! (But I cannot verify.) So I don't have to file a bug report.

---


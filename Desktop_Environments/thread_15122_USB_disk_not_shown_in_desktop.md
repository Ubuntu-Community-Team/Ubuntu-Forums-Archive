---
title: "USB disk not shown in desktop"
date: 2005-02-12
forum: Desktop Environments
---

### Post by GilGalad on 2005-02-12
Hi,

I am running Hoary and I am noticing this strange behaviour. Whenever I connect my USB disk, it is automatically mounted in /media/<name> and a browser window appears. This is ok but the disk icon _does not_ appear on the desktop. It does not appear on the Computer folder either.

The icon appears if I boot with the USB disk plugged.

Also I have mounted my windows partition in /mnt/windows and it is shown in the computer folder as (838M Hard Drive: 838 Media) instead of just windows. If I try to unmount this partition (right click -> unmount) I get an error (that is ok) and the USB disk appears on the Computer folder and in the Desktop.

All the icons appear (and the windows drive is named "windows") if I restart dbus after plugging in the USB disk but then the icons do not dissapear after unmounting the USB disk.

Any hints?

Cheers.

---

### Post by GilGalad on 2005-02-12
I'll reply to myself:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=5176](https://bugzilla.ubuntu.com/show_bug.cgi?id=5176)

---


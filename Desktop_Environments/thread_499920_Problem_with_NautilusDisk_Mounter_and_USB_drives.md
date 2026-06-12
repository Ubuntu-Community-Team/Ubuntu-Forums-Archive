---
title: "Problem with Nautilus/Disk Mounter and USB drives"
date: 2007-07-13
forum: Desktop Environments
---

### Post by Lesterchakyn on 2007-07-13
I'm having this strange problem (**that goes away if I reboot**), but I don't want to do it, neither I want to logout and login from gnome.

Restarting a service is an option tho.

I have an usb powered disk drive, that I mount and unmount from the disk mounter applet (it doesn't work reliably with automount, go figure).  Sometimes I unmount the drive and it gets stuck in the disk mounter applet (also in computer:///), and it appears as "unmounted", but this happens even if I disconnect the drive.  To make things worse, if I connect another usb drive, it doesn't appear in the disk mounter or in Nautilus, so I have to mount it manually, and if I reconnect the disk drive while the icons are stuck, it can be mounted and unmounted without problems (but again, if I disconnect the drive, the icons remain).

Of course, I use the "unmount" option of the Disk Drive Applet.

How can I fix this without having to restart the machine or the gnome session?

Thanks in advance!! :)

---

### Post by mbradlcu on 2007-07-14
kinda funny I just ran into this issue.. I'm not sure how to find my post on it but I tried a bunchOstuff but I think what really fixed this issue was:
```
/etc/init.d/dbus restart
```
my post makes mention of a few modules that I reloaded so check it out if you'd like.

---


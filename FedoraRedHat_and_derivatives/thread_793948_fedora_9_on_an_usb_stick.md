---
title: "fedora 9 on an usb stick"
date: 2008-05-14
forum: Fedora/RedHat and derivatives
---

### Post by karellen on 2008-05-14
I was wondering if I can install Fedora 9 on 1 gb usb stick? I'd like the idea of a portable os. has anyone tried it?

---

### Post by Antman on 2008-05-14
> **karellen said:**
> I was wondering if I can install Fedora 9 on 1 gb usb stick? I'd like the idea of a portable os. has anyone tried it?
For a 1gig stick I would recommend using the livecd-iso-to-disk script that is on the LiveCD iso.
Usage:
> su
sh livecd-iso-to-disk --overlay-size-mb ***256 ***Fedora-9-Live.iso /dev/***usbdevice***

This will create a 256mb persistant layer on the usbstick so you can save your data and settings. I normally format the usbstick as fat so that I can use it on windows systems too.

---

### Post by karellen on 2008-05-14
thanks man :)

---

### Post by jlc on 2008-05-29
Yes, the persistant live usb rocks on F9.

---

### Post by L815 on 2008-06-07
Mine crashes during updates. I reboot, and it's ruined :/
Has happened all 3 times I've tried.

I used the live usb creator that I found from lifehacker.

---

### Post by igknighted on 2008-06-07
> **L815 said:**
> Mine crashes during updates. I reboot, and it's ruined :/
Has happened all 3 times I've tried.

I used the live usb creator that I found from lifehacker.

Don't do updates with a persistant stick... from what I know, you can't replace system files, as they are still part of an ISO image.

---


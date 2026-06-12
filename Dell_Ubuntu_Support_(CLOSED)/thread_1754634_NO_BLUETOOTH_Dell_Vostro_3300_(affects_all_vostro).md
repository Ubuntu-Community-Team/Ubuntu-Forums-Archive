---
title: "NO BLUETOOTH Dell Vostro 3300 (affects all vostro?)"
date: 2011-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ryannathans on 2011-05-10
**FOUND A FIX!**

[SIZE=2]Found what looks like a FIX.

Enabled the bluetooth in Windows 7.

Booted back to ubuntu and it was working!

:D[/SIZE]


-------


11.04 64bit

Dell Vostro 3300

Bluetooth is not detected.

lsusb | grep -i blue

Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 HUB (part of BCM2046 Bluetooth)



tried all the 'solutions' posted on [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/762964](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/762964) [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760203](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760203) [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/770212](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/770212) and [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/771254](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/771254)

none of the solutions help me and not even Bluetooth symbol pops up.

Bluetooth does not detect any bluetooth adapters.

Anyone found a fix?

Thanks!

EDIT: This is an onboard chip

---


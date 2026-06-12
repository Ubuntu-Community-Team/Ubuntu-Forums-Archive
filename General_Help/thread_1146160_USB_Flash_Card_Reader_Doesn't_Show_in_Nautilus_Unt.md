---
title: "USB Flash Card Reader Doesn't Show in Nautilus Until Another Device is Connected"
date: 2009-05-02
forum: General Help
---

### Post by GenuineXP on 2009-05-02
Hi. I have an Alcor 12-in-1 Flash Card Reader/Writer. The different card readers usually show up in Nautilus (in the *Computer* location, along with my optical drive and the root file system). After installing Ubuntu 9.04, they don't appear *until* I connect another USB storage device! Once I power on an external USB hard disk or connect a USB flash memory device, everything shows up.

Even though the card reader isn't displayed, lsusb reports:

```

Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

The card reader is reported at the very top, along with some of the other gizmos attached to my system. After attaching some other USB storage device, the output of lsusb is exactly the same except, of course, that the new device is also reported.

Any ideas why this occurs and what I can do to fix it? Is this some new behavior of Nautilus? Will it only display USB storage devices once one has been mounted?

I realize this is a pretty trivial issue, but I'd like to get it working all the same, or at least understand why it's happening.

Thanks!

Also, lulz at the mistake, "21-in-1".

---

### Post by upptown on 2009-05-08
Try this:
```
 sudo gedit /etc/modules
```

add the following as the last line.  Save then reboot.

```
usb_storage
```

Got the exact same card reader working for me.

---

### Post by GenuineXP on 2009-05-12
Thanks! That seemed to do the trick. I wonder why the usb_storage module wasn't included by default.

---


---
title: "wireless mouse choppy in gnome-shell"
date: 2013-01-02
forum: Desktop Environments
---

### Post by Chris_82 on 2013-01-02
Hi all,

after a crash/freeze of my pc it seems my Logitech wireless mouse started to move choppy in **gnome-shell**.
In **unity** it moves just fine.

dmesg receiver part:
```
[    2.085242] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.3/input2

```

Module hid_logitech_dj is successfully loaded.

The crash might be related to the issue..
Enabling the proposed channel and updating did not help, neither does stopping/starting the module, unplugging/replugging the USB receiver.

I tried booting with mainline kernels 3.5.1 and 3.5.6 with the same results so it is probably not kernel related.

Ubuntu 12.10
3.5.0-21-generic x86_64

Any clues?

---

### Post by Chris_82 on 2013-01-04
Although in French, this is the closest other post I could find:
[http://forum.ubuntu-fr.org/viewtopic.php?id=1078141](http://forum.ubuntu-fr.org/viewtopic.php?id=1078141)

The issue might be hardware related :(

machine: Lenovo Thinkstation E30

---


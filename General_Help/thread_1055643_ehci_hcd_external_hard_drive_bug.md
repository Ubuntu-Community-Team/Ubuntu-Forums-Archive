---
title: "ehci_hcd external hard drive bug"
date: 2009-01-30
forum: General Help
---

### Post by Catalyst2Death on 2009-01-30
Hello,

I have an external hard drive which is affected by the ehci_hcd bug:
[https://bugs.launchpad.net/ubuntu/+bug/184382](https://bugs.launchpad.net/ubuntu/+bug/184382)

Sometimes my disk works fine, but most of the time (nearly 99% of the time) I need to unload ehci_hcd before I can mount the drive.  After some consideration, I decided to try to run the drive via A/C power (it didn't come with a power adapter, just an extra dongle to plug into another usb port)  I now have some new symptoms to report on.

If I run on usb power only, the bug occurs as documented on launchpad.  If I plug the drive in to A/C power, it mounts and runs at normal USB 2.0 speeds.  The interesting bit is, if I unplug the A/C power with the drive mounted, It continues to run on USB 2.0 speeds.  

I've also tried running the drive on USB power, unloading ehci_hcd, mounting the drive and reloading ehci_hcd and the drive un-mounts.  So, it appears that somewhere, the ehci_hcd module doesn't request allow/request the correct amperage to be sent to the external hard drive.  I don't know how this works at all on an implementation level, but at a macroscopic level, this appears to be what is going on.  I'm curious if there is any way to tweak the resources available to the USB devices.

---

### Post by Catalyst2Death on 2009-01-31
*friendly bump*

I  was wondering if anyone else could confirm this behavior, or had an idea of where to start hacking...  I wouldn't mind at least reading the source code.

---


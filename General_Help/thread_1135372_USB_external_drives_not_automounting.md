---
title: "USB external drives not automounting"
date: 2009-04-24
forum: General Help
---

### Post by mathwizard44 on 2009-04-24
I have a Western Digital USB external hard drive that I use with my Linux machine (which originally ran Windows 98SE back in 1999). I have a USB hub that I use to connect the hard drive to the computer.

When I plug in the external hard drive to the computer through the hub, the icon does not show up on the desktop. As I have learned, I opened up a terminal and typed 'lsusb' to get the list of USB devices. The result is this:

```
~$ lsusb
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
~$ lsusb
Bus 001 Device 004: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Yes, I ran the command twice. On the second time I run 'lsusb' the WD entry appears and the hard drive icon appears on my desktop. The problem, of course, is that I have to run lsusb twice before I can access my drive. I checked the Volume Management panel and I made sure that removable drives are mounted as soon as they are plugged in. Is there a setting that I need to look at to make sure that the drive is automounted?

Any help will be appreciated. By the way, I am running Xubuntu 9.04, and it's on a 1999 Gateway desktop computer.

Romel

---

### Post by mathwizard44 on 2010-07-22
I'm bumping this topic, as this behavior is only intermittent. Sometimes the drive appears on the desktop, and other times it doesn't. Any help will be appreciated.

---


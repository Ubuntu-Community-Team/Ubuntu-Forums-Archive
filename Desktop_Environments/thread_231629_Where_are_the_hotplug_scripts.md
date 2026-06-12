---
title: "Where are the hotplug scripts?"
date: 2006-08-07
forum: Desktop Environments
---

### Post by adds2one on 2006-08-07
Hello,

I am wondering two things. First, how can I tell if hotplug is installed? Second, if it is installed where would the hotplug scripts be? I thought that they are normally in /etc/hotplug but they are not there.

I need to know they are working as I am troubleshooting a sound card installation issue with and Echo Audio Indigo IO.

You can see my full post about this at 

[http://www.ubuntuforums.org/showthread.php?t=229778](http://www.ubuntuforums.org/showthread.php?t=229778)

Thank you!

---

### Post by cantormath on 2006-08-07
> **adds2one said:**
> Hello,

I am wondering two things. First, how can I tell if hotplug is installed? Second, if it is installed where would the hotplug scripts be? I thought that they are normally in /etc/hotplug but they are not there.

I need to know they are working as I am troubleshooting a sound card installation issue with and Echo Audio Indigo IO.

You can see my full post about this at 

[http://www.ubuntuforums.org/showthread.php?t=229778](http://www.ubuntuforums.org/showthread.php?t=229778)

Thank you!

Hotplug lets you plug in new devices and use them immediately. That means that users won't need to learn so much system administration; systems will at least partially autoconfigure themselves. Initially, hotplug included support for USB and PCI (Cardbus) devices, and could automatically configure some common network interfaces. Updated versions include IEEE 1394 (Firewire/i.Link) support and can download firmware to USB devices that need it. On mainframes, S/390 channel devices uses hotplugging to report device attach and other state change events. For laptops, newer kernels also include support for reporting docking station activity.
[http://linux-hotplug.sourceforge.net/]("http://linux-hotplug.sourceforge.net/")

---

### Post by adds2one on 2006-08-07
So from reading your link I seem to get that hotplug is actually a part of the the Linux kernel. Does this include the hotplug scripts too?

---

### Post by fdoving on 2006-08-07
As of Ubuntu 6.06 "dapper", hotplug is no longer included in the distribution. It's been replaced by udev+hal.

- Frode

---


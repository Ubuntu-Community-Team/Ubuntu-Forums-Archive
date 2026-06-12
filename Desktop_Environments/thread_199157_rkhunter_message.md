---
title: "rkhunter message"
date: 2006-06-18
forum: Desktop Environments
---

### Post by bobap1950 on 2006-06-18
I get the following when running rkhunter.  I am fairly new to Linux, do I have something to worry about?

* Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)

Thanks for your time.

Bob  :cool:

---

### Post by ardchoille on 2006-06-18
[QUOTE=bobap1950]I get the following when running rkhunter.  I am fairly new to Linux, do I have something to worry about?

* Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)

Thanks for your time.

Bob  :cool:[/QUOTE]

I am a security zealot and run rkhunter, chkrootkit and tripwire on all systems, after a fresh install, before running anything else or connecting any box to the network. I have gotten this same message from rkhunter on every version of Ubuntu I have used. I have also gotten this same message in other distros. I woudln't worry about this particular message.

---


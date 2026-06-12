---
title: "Automount fail to mount **one** USB device"
date: 2008-07-21
forum: Desktop Environments
---

### Post by luckylinux on 2008-07-21
Hi
As you can see in the title my problem is very strange.
Automount mount everything but one device.
The device is labeled "UDISK 2.0" and is from emtec (a 8GB pendrive).
All other drives (external harddisks, pendrives, etc) mount automatically withouth problems.
The error I receive when automount tries to mount that device is:
> Invalid mount option when attempting to mount the volume <<UDISK 2.0>>

I don't have anything in /etc/fstab about it.
I tried to add something to /etc/mtab to see if it would work but nothing changed.
I can only mount the drive under root user, but I cannot mount it in RW/users mode. It's very bad.

Do you have any idea ?
Thanks
Luckylinux

---

### Post by coffeecat on 2008-07-21
I don't have an answer, but a few comments/suggestions.

1 /etc/fstab is nothing to do with dynamic automounting. That tells the system what to mount when it boots up.
(**Edit:** Mepis (used to?) rewrites fstab dynamically, but that's a special case. As far as I know Ubuntu does not.)

2 It's best not to mess with /etc/mtab. That is dynamically rewritten by the system when things are automounted. The fact that you're not getting an entry for your pendrive merely reflects whatever the underlying problem is.

Have you tried mounting this pendrive with another distro or operating system? Have you access to a Windows machine or a Mac? If you don't have another Linux distro installed, have you a live CD of Mandriva or Mepis or openSUSE (for example)? Can you mount the pendrive from a live CD of another distro? Or even better, can you mount the pendrive when you run your Ubuntu CD live?

That might help to decide whether there's a quirk with that particular USB drive, or whether there's something odd happening in your Ubuntu installation.

Last thought. Have you got Gparted installed? Try reformatting the whole drive with Gparted and then trying again.

---

### Post by mcpatu on 2009-05-16
> **coffeecat said:**
> Last thought. Have you got Gparted installed? Try reformatting the whole drive with Gparted and then trying again.

 I had the same problem with the same pendrive. It was properly auto-mounted in Windows and MacOS X, but not in ubuntu.

 After reformatting it under Linux it's also properly auto-mounted in my ubuntu.

---


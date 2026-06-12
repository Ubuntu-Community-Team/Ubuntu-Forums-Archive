---
title: "On startup an USB stick is mounted as root"
date: 2008-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Boldewyn on 2008-07-01
Hi,

I've a Dell Inspiron with Ubuntu 8.04 up and running.

My Problem: When leaving an USB storage stick attached on system shutdown, during the next start it will be mounted as root with rights 700.

That means, other users than root can't open it (ok, thats clear), but even a `sudo chmod 777 /media/usbdisk` fails (no error message, but rights are afterwards again 700).

The only help was an umount and plugin' it in again.

Does anyone know, if there are some preferences to tweak this behaviour? Explaining the other, non-experienced users of my system how umount via terminal works is not an option ;-)

Btw: The stick is formatted as FAT32.

Thanks!

---

### Post by ridgeland on 2008-07-12
I suggest search/learn about udev rules and /etc/fstab.

I used
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)
as a starting point.

udev rules plus /etc/fstab tells my PC how to mount my USB card readers etc.

---

### Post by PinkFloyd102489 on 2008-07-12
Just a tip: Chmodding a mounted dir wont work. You have to umount it, chmod, then remount.

---


---
title: "busybox - what now"
date: 2020-06-19
forum: Desktop Environments
---

### Post by Geoff_Lane on 2020-06-19
Folks,

My main system is Ubuntu 18:04 but I experiment with other distros on an external drive.

On this drive I have Debian, Arch and RaspberryPi for PC all booting fine via a custom GRUB entry on my internal drive.

A recent attempt to install Ubuntu-mate on the external drive has given me a problem, installation from a live image appeared to go fine though seemed to take ages, on booting I always end up with a busybox prompt.

The file system seems to be there, vmlinuz and initrd.img etc. tried manually booting from GRUB command line but always busybox.  I've looked in the /var/log folder of the ubuntu-mate file system but can see no syslog.

I have tried a reinstall but same result.

The live image works fine and the sha256sum checked out OK

Anyone any idea what I could check to resolve this?

Geoff

---

### Post by VMC on 2020-06-19
Edit the linux line for that distro, and remove "quiet", so you can see more messages come across .

---

### Post by Geoff_Lane on 2020-06-29
All working fine now.

Used sudo grub-install and update-grub but followed each with an actual location, eg /dev/sd*n

That installed fine and gave me my grub menu back.

Geoff

---

### Post by anarchy-x on 2020-06-29
Please mark this as Solved.

---

### Post by Geoff_Lane on 2020-06-30
Done.

---


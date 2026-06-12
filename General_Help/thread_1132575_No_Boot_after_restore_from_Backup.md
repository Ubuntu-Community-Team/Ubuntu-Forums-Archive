---
title: "No Boot after restore from Backup"
date: 2009-04-22
forum: General Help
---

### Post by coho on 2009-04-22
After a disk failure I had to reinstall Ubuntu Intrepid  and restore my old configuration from a Backup tar file.
Now when I boot the machine I get the following message:

Gave up waiting for root device.Common problems:
-Boot args (cat /proc/cmdline)
-Check rootdelay=(Did the System wait long enough?)
-Check root=(Did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid/5----and a long number does not exist,
Dropping to a shell

Busy Box v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6)built in shell (ash)

Enter help for a list of commands

initramfs

I tried to create the missing dir /proc/modules but it just 
says: file exists.

I need help to solve this problem.
Than you

---


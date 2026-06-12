---
title: "FakeRAID Grub issues..."
date: 2006-01-02
forum: Desktop Environments
---

### Post by bbrazil on 2006-01-02
I followed the wiki for FakeRAID and grub can't find my root device.  Could someone with SATA FakeRAID working post or PM me their menu.lst file?  Thanks.

---

### Post by realriot on 2006-01-05
When you've configured your grub you can do "update-grub"... This will configure and install the needed menu.lst for your installation.

The problem:
update-grub can't detect your root-dervice and assumes that it is hda1. You've got to change it to your root-device which you've configured for your raid.
Just edit the menu.lst file.

best wishes
Sascha

---

### Post by bbrazil on 2006-01-06
My devices are set up as follows:

/dev/mapper/nvidia_eecgdbfe1 - boot 
/dev/mapper/nvidia_eecgdbfe2 - swap
/dev/mapper/nvidia_eecgdbfe3 - root 

In /boot/grub/menu.lst, I have the followiot defined:

kernel    /vmlinuz-2.6.12.10-amd64-k8 root=/dev/mapper/nvidia_eecgdbfe3 ro splash

The kernel seems to load fine.  The Ubuntu loading screen comes up and goes through loading modules and setting up dev.  When it gets to setting up the root partition, it drops out to a shell.  Here is a snippet of what I get (when the trouble seems to start):

Booting the kernel.
Loading, please wait...
ERROR: device-mapper target type "mirror" not in kernel
ERROR: dos: reading /dev/mapper/nvidia_eecgdbfe[No such file or directo
  /dev/cdrom: open failed: No medium found
  /dev/dcrom1: open failed: No medium found
  Unable to find volume group "nvidia_eecgdbfe3"
ALERT! /dev/mapper/nvidia_eecgdbfe3 does not exist. Dropping to a shell

It seems to be able to find nvidia_eecgdbfe1 fine, but cannot find nvidia_eecgdbfe3

Any suggestions?

---

### Post by bbrazil on 2006-01-11
The solution is in this thread:

[http://www.ubuntuforums.org/showthread.php?p=647543](http://www.ubuntuforums.org/showthread.php?p=647543)

---


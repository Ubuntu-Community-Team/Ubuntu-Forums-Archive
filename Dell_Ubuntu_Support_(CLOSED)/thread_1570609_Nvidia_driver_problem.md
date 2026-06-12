---
title: "Nvidia driver problem"
date: 2010-09-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Muchoaliento on 2010-09-08
Hi there,

Installed 10.04 64b fresh on my xps 1330 which has Geforce 8400M GS video card.
Of course I installed nvidia hardware controllers which were 173 version I think.
After a while I began having too many problems such as freezes and crashes.
I tried to update nvidia drivers to latest version doing 

1. sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
2. sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

which apparently did nothing as they did not show under hardware drivers. Doing a purge solved this.
This is my sudo lshw -C video output:
description: VGA compatible controller
       product: G86 [GeForce 8400M GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff(prefetchable) memory:fa000000-fbffffff ioport:ef00(size=128) memory:fc000000-fc01ffff(prefetchable)

where it states driver as "noveau" Is this correct ? Shouldnt it say "235" or something like that ?
Another problem I am having is that I cannot access nvidia control panel, I do not have its link under "system" and when I try to execute nvidia-settings command, the following error message appears:
"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Any help is welcome ! :p Thanks in advance

---

### Post by Muchoaliento on 2010-09-08
How do I move this post to the Video & Multimedia category ?

---

### Post by realzippy on 2010-09-08
[I]...Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
[/I]

```
sudo nvidia-xconfig
```
reboot..

Any luck?

---

### Post by Muchoaliento on 2010-09-08
Says "command not found"

---

### Post by realzippy on 2010-09-09
..so the nvidia-driver indeed is not installed.
What driver is offered in System/Administration/Hardwaredrivers?

---


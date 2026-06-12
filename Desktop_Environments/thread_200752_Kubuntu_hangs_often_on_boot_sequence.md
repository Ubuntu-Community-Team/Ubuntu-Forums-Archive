---
title: "Kubuntu hangs often on boot sequence"
date: 2006-06-20
forum: Desktop Environments
---

### Post by kalahari875 on 2006-06-20
I have a Kubuntu 6.06 installation patched current that often, but not always, hangs at a random spot during the boot sequence when the graphical Kubuntu boot sequence screen is up. Often it occurs after "Mounting root filesystem," but it has also occurred after "Setting up ALSA utils" and at other spots. When this occurs, the screen freezes and the machine will not respond to Ctrl+Alt+Del. If I force a reboot by cutting power, often on the second attempt it will boot just fine.

I would blame the hardware, except that it was fine before the upgrade from Breezy, and it never crashes once I get it to boot (it will stay up for weeks at a time). Since it seems to occur more often on the mounting root filesystem entry, I am tempted to think something's wrong with one of the disks (two HDDs in a RAID 1 configuration managed by mdadm). However, fsck ran over the disk on boot the other day, and it found no errors. 

Can anyone suggest what I can do to diagnose this problem? Also, what's the best way to run fsck over the drives--do I need to boot from the live CD, and then what? 

Here's my mdadm.conf in case it helps:
[INDENT]DEVICE partitions
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=eb983c4f:69bff162:ad0e9e1b:85935800
   devices=/dev/hda6,/dev/hdc6
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=f04894f4:b443411d:1117513d:a0574c0d
   devices=/dev/hda5,/dev/hdc5
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=a5d3c0be:0c381cce:9c190068:e5e952b1
   devices=/dev/hda1,/dev/hdc1[/INDENT]

Thanks!

---


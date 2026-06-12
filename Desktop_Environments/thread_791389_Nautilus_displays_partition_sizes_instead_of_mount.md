---
title: "Nautilus displays partition sizes instead of mount point names"
date: 2008-05-12
forum: Desktop Environments
---

### Post by larryni on 2008-05-12
Before Hardy Nautilus used to display the names of the partitions as specified in fstab in the Places side pane, e.g. 'sda1'. Now it only displays the partition sizes, e.g. '300 GB Media'. I get back to the old way?

---

### Post by chunchengch on 2008-05-12
1. make the corresponding directory in /media for the partition/media you want to mount and to display in the Nautilus side pane, for example, /media/sda1 for /dev/sda1 (300 GB Media).

2. confirm your file system and then type the command to set the new label,

for ext2/ext3 :

[COLOR="Red"]$ sudo e2label /dev/sda1 sda1[/COLOR]

for reiserfs :

[COLOR="Red"]$ sudo reiserfstune -l sda1 /dev/sda1[/COLOR]

---

### Post by larryni on 2008-05-13
I was able to change the label on just one partition.  I keep getting the following message on the partitions of my 2 other drives:

```
e2label: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
```

I did have problems with the boot loader installing properly and had to edit grub manually. Could this have something to do with it?

---

### Post by larryni on 2008-05-13
Actually, changing the label of the partition didn't change my original problem. Places still shows the partition size and not the label I assigned it, even after logging off/on.

---

### Post by Awalton on 2008-05-14
Should try restarting. I believe the HAL stuff for persistent mounts only updates on reboot/explicit restart of hald, but I'm not a HAL expert (and, quite frankly, I don't think anyone is these days...)

I'm definitely getting the correct labels here anyways (for ext3, fat32 and reiser volumes). Otherwise it could be a bug in gvfs-hal.

---


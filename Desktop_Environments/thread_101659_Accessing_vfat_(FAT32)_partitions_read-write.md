---
title: "Accessing vfat (FAT32) partitions read-write"
date: 2005-12-10
forum: Desktop Environments
---

### Post by biteydog on 2005-12-10
I need to mount my Windows partition read/write to user, not root. I've done the usual thing and changed /etc/fstab to read

/dev/hda1/      /windows       vfat       rw, auto,user      0  0

which always worked in other linuxes, but I assume there is some 'safety' feature preventing me, because it mounts ro except for root. Can anyone tell me what it is? (And how to disable it?)

Compaq Armada 7400 laptop P11-300,256M,6G, ethernet card, wireless card.

Windows partition has Windows CD driver and other W98 drivers installed, no W98SE installed (yet)

---

### Post by biteydog on 2005-12-10
OK -managed to find it in the Wiki in the end - sorry!

/dev/hda1   /windows   vfat   user,fmask=0111,dmask=0000   0   0

---

### Post by aysiu on 2005-12-10
Unmount it first: ```
sudo umount /windows
``` Then ```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Replace this line: [QUOTE=biteydog]
/dev/hda1/      /windows       vfat       rw, auto,user      0  0
[/QUOTE] with this one ```
/dev/hda1  /windows   vfat   umask=000   0   0
``` Save and then ```
sudo mount -a
```

---


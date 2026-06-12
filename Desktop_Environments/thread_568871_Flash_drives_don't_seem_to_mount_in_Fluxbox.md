---
title: "Flash drives don't seem to mount in Fluxbox"
date: 2007-10-06
forum: Desktop Environments
---

### Post by fnfal on 2007-10-06
When I'm logged in using Fluxbox and plug in a flash drive, it doesn't show up in /media which makes me think it's not mounting at all.  It does work in gnome; what can I do to make it usable in fluxbox?

---

### Post by taurus on 2007-10-06
You can always try to mount it by hand.

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by fnfal on 2007-10-06
Here's the output:
```
fnfal@ibm3f954t43:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20480008+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2550        3083     4278960   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            3084        4787    13687380   83  Linux
/dev/sda4            4788        4864      618502+   5  Extended
/dev/sda5            4788        4864      618471   82  Linux swap / Solaris

Disk /dev/sdb: 2063 MB, 2063597056 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         251     2015200    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(249, 254, 63) logical=(250, 225, 38)
```
I had thought of doing it by hand, but since I'm relatively new with this I was having trouble finding detailed instructions.

---

### Post by taurus on 2007-10-06
From a terminal, run

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o iocharset=utf8,umask=000
ls -la /media/sdb1
```

---

### Post by fnfal on 2007-10-06
It looks like it's working; thanks for your help.

---

### Post by taurus on 2007-10-06
You're welcome.

---


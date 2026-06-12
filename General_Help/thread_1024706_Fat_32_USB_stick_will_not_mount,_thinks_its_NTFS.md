---
title: "Fat 32 USB stick will not mount, thinks its NTFS?"
date: 2008-12-29
forum: General Help
---

### Post by Julian David Pitt on 2008-12-29
USB Flash memory stick won't mount on insertion?
I have a Corsair flash voyager memory stick that refuses to mount. Please see attached image for the error message I receive. The drive is fat32 but Intrepid seems to think it is NTFS in the error message. However if I do


```
fdisk -l
```

I get


```
Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   IdSystem
/dev/sdb1   *           1         984     7897056+   bW95 FAT32
Partition 1 has different physical/logical endings:
     phys=(982, 254, 63) logical=(983, 36, 13)
```

At some point I also get the DBUS error in the second image, sorry not sure what brought it up though. This problem has been with me since I upgraded from Hardy.. Your help is much appreciated.

---

### Post by taurus on 2008-12-29
What happens if you try to mount it from a terminal?

Applications -> Accessories -> Terminal
```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by Julian David Pitt on 2008-12-29
> **taurus said:**
> What happens if you try to mount it from a terminal? 

I get special device /dev/sdb1 does not exist?

---

### Post by Julian David Pitt on 2008-12-29
Just tried rebooting the laptop and this time it found the stick when I did fdisk -l and would let me mount it when I used your command. To my way of thinking something is not running until I reboot, whereupon the stick is found. Your thoughts are appreciated my friend.

---


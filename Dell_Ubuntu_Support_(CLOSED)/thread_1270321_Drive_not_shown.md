---
title: "Drive not shown"
date: 2009-09-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Vishnu V on 2009-09-19
hai
I bought a new Dell studio 15 laptop and i formated vista and installed ubuntu on it
now i have 4 drives(including swap)
but in places menu i cannot find one drive
output of ```
sudo fdisk -l
```
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6225    50002281   83  Linux
/dev/sda2            6226       38913   262566360    5  Extended
/dev/sda5            6226        6599     3004123+  82  Linux swap / Solaris
/dev/sda6            6600        9089    20000893+   b  W95 FAT32
/dev/sda7            9090       38913   239561248+   b  W95 FAT32
vishnu@vishnu-laptop:~$ 

```

pls help
Thanks in advance

---

### Post by Vishnu V on 2009-09-19
Sorry !!
that drive was not properly formated that was the problem. and now i formated it and can take it from places menu

---


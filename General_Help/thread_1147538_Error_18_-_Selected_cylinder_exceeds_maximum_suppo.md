---
title: "Error 18 - Selected cylinder exceeds maximum supported by BIOS"
date: 2009-05-03
forum: General Help
---

### Post by khaledkhal on 2009-05-03
Hi Guys,

I have a problem that has been facing me for quite a while. Right now I decided to not work on windows at all :D and install only ubuntu on my desktop, but when I did, and finished installation, I got this error message after rebot:

```
Error 18 - Selected cylinder exceeds maximum supported by BIOS
```

I searched over the net, and I went into the BIOS settings and in the HD menu it is set to Automatic. and when I did 
```
sud0 fdisk -l
```
 from the terminal using the Live CD, this is what I got.

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31b031af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4619    37102086   83  Linux
/dev/sda2            5171       19456   114752295    5  Extended
/dev/sda3            4620        4805     1494045   82  Linux swap
/dev/sda5            5171       12811    61376301    7  HPFS/NTFS
/dev/sda6           12812       15990    25535286    7  HPFS/NTFS
/dev/sda7           15991       19456    27840613+   7  HPFS/NTFS

Partition table entries are not in disk order


```

What should I do now???

---


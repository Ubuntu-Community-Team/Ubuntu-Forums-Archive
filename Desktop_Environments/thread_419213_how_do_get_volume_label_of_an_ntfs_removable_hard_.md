---
title: "how do get volume label of an ntfs removable hard disk?"
date: 2007-04-22
forum: Desktop Environments
---

### Post by stock99 on 2007-04-22
Hi,

   I have setup the 'fuse' & 'ntfs-3g' and i have no problem on mounting and un-mounting my NTFS formated removable hard drive disk.   But i am not sure what command i can use do display the VOLUME LABEL of a particular disk I connected.

   Is there any command can display such info? Since i using those HD for backup purpose, and my script is going to be relayed on volume label to differentiate one to another.

Thanks in advance.



Chris

---

### Post by vonlogik on 2008-04-30
```
sudo vol_id /dev/your_volume_here
```

For example, on my system:
logik@logikdt-ub:/media$ sudo vol_id /dev/sdf1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ntfs
ID_FS_VERSION=3.1
ID_FS_UUID=80845F34845F2BC2
ID_FS_UUID_ENC=80845F34845F2BC2
**ID_FS_LABEL=EX2**
ID_FS_LABEL_ENC=EX2
ID_FS_LABEL_SAFE=EX2
logik@logikdt-ub:/media$ 

:guitar:

---


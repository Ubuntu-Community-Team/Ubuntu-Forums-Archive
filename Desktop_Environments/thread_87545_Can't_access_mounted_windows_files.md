---
title: "Can't access mounted windows files"
date: 2005-11-08
forum: Desktop Environments
---

### Post by sfpiano on 2005-11-08
I mounted my windows drive, and I can ls it to see the contents, but when I try to cd into the directory, it tells md cd: command not found.

Here's my fdisk output:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       11606    93217162+   f  W95 Ext'd (LBA)
/dev/sda2   *       11607       14593    23993077+  83  Linux
/dev/sda5               2       11475    92164873+   7  HPFS/NTFS
/dev/sda6           11476       11606     1052226   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS

```

And I called:
sudo mount /dev/sdb1 /mnt/win/ -t ntfs -o nls=utf8,umask=0222

---

### Post by shinygerbil on 2005-11-08
Try umask 0022

Steve

---

### Post by shinygerbil on 2005-11-08
EDIT: double post --delete

---


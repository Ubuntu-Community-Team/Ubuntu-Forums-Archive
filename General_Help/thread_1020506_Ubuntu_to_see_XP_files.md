---
title: "Ubuntu to see XP files?"
date: 2008-12-24
forum: General Help
---

### Post by Saddl3r on 2008-12-24
Hi, im now on a Live CD "trial" (Havent installed Ubuntu yet) So is it possible for it to see my windows XP Files? My XP "died" today, so i need to access my files with Ubuntu.

---

### Post by northern lights on 2008-12-24
It is possible indeed.

ntfs partitions other than the Windows system one should mount out of the box.

Most likely, your Windows drive/partition's device identifier is sda1. You can run```
blkid
```from a terminal to list all storage devices. Mount the drive/partition via ```
sudo mount /dev/sda1
```or whatever device it may be.

---

### Post by Saddl3r on 2008-12-24
> **northern lights said:**
> It is possible indeed.

ntfs partitions other than the Windows system one should mount out of the box.

Most likely, your Windows drive/partition's device identifier is sda1. You can run```
blkid
```from a terminal to list all storage devices. Mount the drive/partition via ```
sudo mount /dev/sda1
```or whatever device it may be.

Nothing happens when i write ```
blkid
``` and if i write ```
sudo mount /dev/sda1
``` it just says ```
mount: can't find /dev/c in /etc/fstab or /etc/mtab
```

---

### Post by northern lights on 2008-12-24
Rather than *blkid*, can you check and/or post the output of```
sudo fdisk -l
```

---

### Post by Zack McCool on 2008-12-24
and your mount won't work unless you give it somewhere to mount...

```
sudo apt-get install ntfs-3g
sudo mkdir /media/xp
sudo mount /dev/sda1 /media/xp -t ntfs-3g -o umask=0222

```

I'm not 100% sure on the umask, but from memory it looks about right.  And, of course, this will only work if your xp partition is sda1.

---

### Post by Barriehie on 2008-12-24
Also remember that *nix and XP file permissions are different. 

Barrie

---

### Post by northern lights on 2008-12-24
> **Barriehie said:**
> Also remember that *nix and XP file permissions are different.
Which means you can't chmod ntfs partitions. Since Gutsy however, ntfs read/write access works out of the box.

---

### Post by Saddl3r on 2008-12-24
> **northern lights said:**
> Rather than *blkid*, can you check and/or post the output of```
sudo fdisk -l
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x059f059e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS





Thanks guys! Its working :D

---


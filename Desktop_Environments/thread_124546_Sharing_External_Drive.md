---
title: "Sharing External Drive"
date: 2006-02-01
forum: Desktop Environments
---

### Post by aseem_mal on 2006-02-01
Hi. I recently installed Ubuntu on my laptop. I have this External Hard Drive (USB). I used it on my Win XP earlier. I need to copy some of my files from Ubuntu to this external drive, but it doesn't allow me. Permission Denied. What can I do to enable write permissions on the Drive?:confused: 

Thanks,
A

---

### Post by Ramses de Norre on 2006-02-01
Is it just that you don't have permissions? Probably only root has write rights then. You could run ```
 sudo chmod a=rwx /mnt/[mountpoint] 
``` to enable full permissions for everyone on the disc (asuming it's not a public computer this isn't really unsafe).

You say you used the disc in win xp, is it an ntfs disc? In that case you should format it with an other filesystem to be able to write on it, linux can't write on ntfs partitions.. you could use fat32 which can be used by win xp and linux or you can use ext3 and install ext2IFS from [http://www.fs-driver.org/]("http://www.fs-driver.org/") in windows, you can then read and write the ext3 partition from windows.

---

### Post by aseem_mal on 2006-02-01
[QUOTE=Ramses de Norre]Is it just that you don't have permissions? Probably only root has write rights then. You could run ```
 sudo chmod a=rwx /mnt/[mountpoint] 
``` to enable full permissions for everyone on the disc (asuming it's not a public computer this isn't really unsafe).

You say you used the disc in win xp, is it an ntfs disc? In that case you should format it with an other filesystem to be able to write on it, linux can't write on ntfs partitions.. you could use fat32 which can be used by win xp and linux or you can use ext3 and install ext2IFS from [http://www.fs-driver.org/]("http://www.fs-driver.org/") in windows, you can then read and write the ext3 partition from windows.[/QUOTE]

Ok... can you tell where will I find what to type as "mountpoint" in the command you gave?
Also, is there a command to find out if the drive is fat32 or ntfs?

---

### Post by aysiu on 2006-02-01
[QUOTE=aseem_mal]Ok... can you tell where will I find what to type as "mountpoint" in the command you gave?[/quote] Plug it in, and type ```
df -h
```
> 
Also, is there a command to find out if the drive is fat32 or ntfs? Plug it in, and type ```
sudo fdisk -l
``` I don't think, if it NTFS or FAT32 that a *chmod* command will do much good. The permissions for those drives and partitions has to do with how it's mounted in your /etc/fstab file. See the fourth link of my signature for more details.

---

### Post by aseem_mal on 2006-02-02
Plug it in, and type ```
df -h
```
 Plug it in, and type ```
sudo fdisk -l
``` [QUOTE=aysiu]I don't think, if it NTFS or FAT32 that a *chmod* command will do much good. The permissions for those drives and partitions has to do with how it's mounted in your /etc/fstab file. See the fourth link of my signature for more details.[/QUOTE]

Hi. After running sudo fdisk -l,  I got the following:

Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       14596   117234337+   f  W95 Ext'd (LBA)
/dev/sda5               2       14596   117234306    7  HPFS/NTFS

Is there a way to enable write access for Ubuntu, without having to re-partition the ext. hard drive?

---


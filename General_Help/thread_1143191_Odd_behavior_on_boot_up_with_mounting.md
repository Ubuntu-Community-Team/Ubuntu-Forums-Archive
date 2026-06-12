---
title: "Odd behavior on boot up with mounting"
date: 2009-04-29
forum: General Help
---

### Post by Nano_ext3 on 2009-04-29
On bootup , the part at the splash that says "mounting local file systems" fails.  Now I know "storage, windows drive, and mnt" are all mounted because I can browse them all.  I do not understand what is not being mounted or what is happening.

fstab

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
#/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
#/dev/fd0               /media/fl   auto    user,noauto             0      0

UUID=AE846F33846EFCE9   /mnt/Windows_Drive      ntfs-3g defaults 0 0 
UUID=bd6757f6-06a5-4c65-a6de-04b32a1d1ad7 / ext4 defaults 0 1
UUID=f3253146-ce38-4cd0-ba00-5ad08873088e swap swap defaults 0 0
UUID=0830EB9330EB8652 /mnt/Storage ntfs-3g defaults 0 0 
#https://webdav.pct.edu/        /mnt/Webdav     davfs2 user,noauto,rw 0 0
/etc/fstab (END) 


```

And my blkid:

```
mikeyd@mikeyd-laptop:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="AE846F33846EFCE9" TYPE="ntfs" 
/dev/sda2: UUID="0830EB9330EB8652" LABEL="Storage" TYPE="ntfs" 
/dev/sda3: UUID="bd6757f6-06a5-4c65-a6de-04b32a1d1ad7" TYPE="ext4" 
/dev/sda5: TYPE="swap" 
```

---

### Post by buchan on 2009-04-29
The only other entry is your swap... 
whats the output of the "free" command?

---


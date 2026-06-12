---
title: "NTFS partition randomly (?) unmounted"
date: 2009-05-10
forum: General Help
---

### Post by mrowth on 2009-05-10
I have this NTFS partition here:

LABEL=bigshared /mnt/collect ntfs defaults,umask=002,uid=1000,gid=114,auto,rw,nouser 0 1

(I'm sure there's something stupid about those options)

Ever since going to Jaunty I often find it unmounted through no fault of my own.

I have another NTFS partition and it's not suffering from that effect (as far as I can tell, I rarely use it).

Anyone have any idea why or how to stop that from happening?

---

### Post by KhurramM on 2009-05-10
If u can convert it to Fat32.

Fat32 is recognized by all OSes around the globe: MAC, win, Linux, unix-variants, solaris

Additionally its very less faulty for other OSes then win.

---

### Post by tama00 on 2009-05-10
Mount the drive back for the meantime, next time you notice it missing i want you to check your system logs. */var/logs/messages *with you fav text editor. Paste the last 500 or so lines into a pastebin website and link it here and we can check that out. Also paste us the output of *fdisk -l*

---

### Post by mrowth on 2009-05-10
fdisk -l

```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02ce02ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       10010    59922450    f  W95 Ext'd (LBA)
/dev/sda5            2551        6374    30716248+   7  HPFS/NTFS
/dev/sda6            6375       10010    29206138+   b  W95 FAT32

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ee6b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         261     2096451   82  Linux swap / Solaris
/dev/sdb2             262        3908    29294527+  83  Linux
/dev/sdb3            3909       44994   330023295    7  HPFS/NTFS
/dev/sdb4           44995       48641    29294527+  83  Linux

```

(The partition in question is sdb3)

Oh no... another question! Can I still add partitions to sdb? Would I need to redo it all with an extended partition?

> **KhurramM said:**
> If u can convert it to Fat32.

Fat32 is recognized by all OSes around the globe: MAC, win, Linux, unix-variants, solaris

Additionally its very less faulty for other OSes then win.

It's too big for FAT32, I think. Or some files on it are too big. One of those...

---


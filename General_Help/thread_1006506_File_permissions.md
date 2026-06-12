---
title: "File permissions"
date: 2008-12-09
forum: General Help
---

### Post by stonedparadox on 2008-12-09
im having trouble deleting files off 2 of my externals in ubuntu 8.10

and secondly one of my externals is showing up twice and when i access it
one is blank and one has my stuff in it
why is it doing that?


i tried logging in via root and doing this
but this happens

root@xxxx://media/EXTERNAL 42_# sudo rm -rf Huge\ Symbian\ Collection/
rm: cannot remove `Huge Symbian Collection/Huge-Symbian OS.Releases.rar': Read-only file system
rm: cannot remove `Huge Symbian Collection/Torrent downloaded from Demonoid.com.txt': Read-only file system
root@xxxx://media/EXTERNAL 42_# 


i was on this page
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
reading all about permissions and its a bit confusing
but i dont think my answer lies there?

---

### Post by psusi on 2008-12-09
It looks like something is wrong with the filesystem so it was remounted read only.  Check the output of dmesg for errors.

---

### Post by taurus on 2008-12-09
What filesystem is that harddrive?

```
sudo fdisk -l
mount
```

---

### Post by stonedparadox on 2008-12-09
> **psusi said:**
> It looks like something is wrong with the filesystem so it was remounted read only.  Check the output of dmesg for errors.

i get kernal panic errors
want the full log?

---

### Post by stonedparadox on 2008-12-09
root@mdma://# sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f53283b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36296   291547588+  83  Linux
/dev/sda2           36297       36483     1502077+   5  Extended
/dev/sda5           36297       36483     1502046   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc1c3c8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    6  FAT16

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a8ca20f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48641   390708801    b  W95 FAT32

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe08679eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001    7  HPFS/NTFS


the 300 gigger is what ubuntu is sitting on

---

### Post by psusi on 2008-12-09
If you paste a few of the errors it would help of course, but it looks like you've got a damaged filesystem and need to fsck it.

---

### Post by stonedparadox on 2008-12-09
which is damanged?

the external or the 300 gig hd?

because the 300 is sorta on the  way out 

but 
heres the dmesg

[15774.507297] FAT: Directory bread(block 190812) failed
[15774.507536] FAT: Directory bread(block 190813) failed
[15774.507773] FAT: Directory bread(block 190814) failed
[15774.508016] FAT: Directory bread(block 190815) failed
[15774.508254] FAT: Directory bread(block 190816) failed
[15774.508487] FAT: Directory bread(block 190817) failed
[15774.508727] FAT: Directory bread(block 190818) failed
[15774.508965] FAT: Directory bread(block 190819) failed
[15774.509202] FAT: Directory bread(block 190820) failed
[15774.509218] FAT: Directory bread(block 190821) failed
[15774.509231] FAT: Directory bread(block 190822) failed
[15774.509245] FAT: Directory bread(block 190823) failed
[15777.469229] FAT: Filesystem panic (dev sdd1)
[15777.469238]     fat_get_cluster: invalid cluster chain (i_pos 0)
[15777.472320] FAT: Filesystem panic (dev sdd1)
[15777.472331]     fat_get_cluster: invalid cluster chain (i_pos 0)
[15807.229650] FAT: Filesystem panic (dev sdd1)
[15807.229660]     fat_get_cluster: invalid cluster chain (i_pos 0)
[15815.055879] FAT: Directory bread(block 190760) failed
[15815.055902] FAT: Directory bread(block 190761) failed
[15815.055914] FAT: Directory bread(block 190762) failed
[15815.055926] FAT: Directory bread(block 190763) failed
[15815.055939] FAT: Directory bread(block 190764) failed
[15815.055953] FAT: Directory bread(block 190765) failed
[15815.055966] FAT: Directory bread(block 190766) failed
[15815.055979] FAT: Directory bread(block 190767) failed
[15815.055992] FAT: Directory bread(block 190768) failed


thats only some of it

---

### Post by psusi on 2008-12-09
Since it is fat, I'd guess the external one, and it's the filesystem that is corrupt, not the disk that is damaged.

---

### Post by stonedparadox on 2008-12-09
how would it of become damaged?

i could just copy everything over to the other drive and format it?

what can i do?

---

### Post by psusi on 2008-12-09
Did you unplug it without unmounting it?  Run a chkdsk on it from windows, or fsck.vfat in Linux.

---


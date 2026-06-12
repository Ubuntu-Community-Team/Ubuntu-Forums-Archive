---
title: "Help recovering data files from Wubi install"
date: 2009-03-11
forum: General Help
---

### Post by Cuba71 on 2009-03-11
I need to recover data files from my Ubuntu 8.10 installation on my Toshiba laptop HDD.
This installation was done using Wubi, and it boots up to a black screen.
This is the output of fdisk -l

[I]Disk /dev/sda: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x6d702ecc 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1         192     1536000   27  Unknown 
Partition 1 does not end on cylinder boundary. 
/dev/sda2   *         192       14594   115683328    7  HPFS/NTFS 

Disk /dev/sdb: 4126 MB, 4126146560 bytes 
16 heads, 32 sectors/track, 15740 cylinders 
Units = cylinders of 512 * 512 = 262144 bytes 
Disk identifier: 0x03aad310 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1       15740     4029424    c  W95 FAT32 (LBA) [/I]

I'm able to boot up using a pendrive.
I've gone as far as mounting /dev/sda2 and found root.disk and root.share under /ubuntu/disks/shared.

Any help will greatly appreciated.
Thank you, Antonio

---

### Post by Cuba71 on 2009-03-11
Thank you for your attention, I already found out how to recover files.

---

### Post by jonathanmotes on 2009-03-23
Could you please explain how you solved your problem?

Thanks!

---


---
title: "lost my old jaunty partition"
date: 2009-05-10
forum: General Help
---

### Post by DNAtsol1 on 2009-05-10
I was too clever by half. 

I had my 9.04 running and wanted to reclaimed my old partition so I ran gparted, removed my old partition, moved my new partition and extended it into the emptied spaced...

Can you guess where this is going? Correct! 

When I rebooted I got a grub error 22. I messed (and I do mean messed) with trying to reinstall the grub, vi'd some of the menu.lst & basically screwed everything and had not record of what I did. So, I reinstalled 9.04, thinking I would just partition off the old jaunty and copy the files over to the new jaunty and lose ~5GB of partition (until I became more proficient). 

Reinstall went well, but the old partition is not there. When I try to boot into it from grub (recovery mode for the old partition) I get /home not there errors and when I try to find it in the new install I can't find it in the place I've put backed up files the last three times I did a jaunty reinstall (mount partition @ /home). 

Any suggestions on how to locate and/or mount this partition so I can get my data (I promise to always backup my files from now on :) )

Thanks
DNAtsol

---

### Post by tama00 on 2009-05-10
Can you paste the output of *sudo fdisk -l* please thanks.

---

### Post by DNAtsol1 on 2009-05-10
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c291c28

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27357   219745071    7  HPFS/NTFS
/dev/sda3           27358       38913    92823570    5  Extended
/dev/sda5           27358       29235    15084972   83  Linux
/dev/sda6           38428       38913     3903763+  82  Linux swap / Solaris
/dev/sda7           29236       29758     4200966   83  Linux
/dev/sda8           29759       38427    69633711   83  Linux

The "old" jaunty is on sda7 (~4.3GB)
thanks

---

### Post by DNAtsol1 on 2009-05-10
As an added piece of info. I can see the partition in my 8.10 partition but 8.10 uses ext3 while my 9.04 partitions are using ext4... if there was some way of mounting an ext 4 on ext3 I might be able to move files but since I cannot mount the partition I could also get similar errors. but at least I can see the partition....

---


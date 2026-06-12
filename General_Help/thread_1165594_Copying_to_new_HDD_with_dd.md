---
title: "Copying to new HDD with dd?"
date: 2009-05-20
forum: General Help
---

### Post by blazercist on 2009-05-20
Here's the situation, I have an old SATA1 WD Raptor HDD (74GB @10,000RPM) Here's the fdisk -l output:

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9e2ea24

I bought a new Western Digital VelociRaptor WD3000HLFS(300GB  @10000 RPM)

I want to hook it up, boot into my existing install and issue the following command:

sudo dd if=/dev/sda of=/dev/sdb

1.  This will copy my MBR /boot / and /home correct?
2.  I will need to change the UUID's in menu.lst on /dev/sdb to match those of that drive?
3.  Will I be able to resize /home to take up the remaining free space? (I dont need to resize /boot or / they are fine)
4.  Will I be able to then physically remove /dev/sda (formerly) and replace it with /dev/sdb thus making what was /dev/sdb into /dev/sda? 
5.  Will it boot?
6.  Outside of human error is there any danger to the original /dev/sda from the dd command? (From what I understand dd only reads on "if" so there shouldn't be any danger but perhaps I'm wrong)
7.  Finally if all the preceding stuff works, will I be able to convert to EXT4?

If I've left any useful info out please let me know.  Thanks in advance.

---

### Post by geirha on 2009-05-20
1. Yes, but the MBR also contains the partition table. Not sure how well that works when the disks are of different size.
2. No, the UUIDs will stay the same, since the filesystems will be unchanged
3. Yes, if /home is the last partition (otherwise, you'll need to move around the other partitions first)
4. Should work.
5. It should, yes.
6. No more danger than any other read operation from the disk.
7. Yes, but if you convert /boot, you might need to install a newer version of grub that can read ext4.

---


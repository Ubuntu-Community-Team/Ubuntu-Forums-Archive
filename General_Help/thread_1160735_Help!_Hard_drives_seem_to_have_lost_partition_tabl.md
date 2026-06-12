---
title: "Help! Hard drives seem to have lost partition table!"
date: 2009-05-15
forum: General Help
---

### Post by GrimRe on 2009-05-15
Recently my motherboard on my ubuntu 8.10 fileserver died. I have 2 linux software raids, 1 RAID1 with 2x320GB hard drives and 1 RAID5 with 3x 1TB hard drives.

I rebuilt the machine with a new P45 motherboard and intel cpu. I tried booting into the first RAID1 device but didn't work so I booted into a ubuntu live cd usb stick. which also strangely enough didn't work the first few times until I fiddled with BIOS settings.

Anyway, got in and tried to rebuild the arrays. To suprise I got this from a fdisk -l

```
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e512c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table

Disk /dev/sdf: 2006 MB, 2006974464 bytes
16 heads, 32 sectors/track, 7656 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          16        7656     1955904    b  W95 FAT32

```

as you see only /dev/sdd seems to have a valid partition!

I really don't want to loose all my data, is there any way to recover the partitions on the disks?

Thanks in advance.

---

### Post by fjgaude on 2009-05-17
I don't think **fdisk** understands drive tables that have been put into **mdadm** arrays.

Here's something to try:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

This should create a new **mdadm.conf** file that is correct. The issue is that the array UUIDs have been changed. These are not the UUIDs used to mount individual drives but to assemble arrays by mdadm. So...

Reboot and see what happens.

Let us know how you are doing.

---

### Post by GrimRe on 2009-05-19
I don't think mdadm needs the disk to be partitioned and seems they never were in the first place. 

if I look at my cat /proc/mdstat output its uses a combination of entire disks (sda) and some partitions (sdb1) which I guess is a bit strange.

I might have to backup all my data and re-format each drive.

Thanks for the help.

---


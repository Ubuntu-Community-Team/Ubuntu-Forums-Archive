---
title: "Mount fat32 - where'd it go?"
date: 2006-07-03
forum: Desktop Environments
---

### Post by Shampyon on 2006-07-03
I've had my 160GB hard drive divided into 4 sections since before I started using Ubuntu. I decided to set them aside this:
Partition 1 - Windows XP Pro
Partition 2 - General Shared Files
Partition 3 - Shared "My Documents" folder
Partition 4 - Ubuntu

I originally had all of my Windows partitions as NTFS. I converted partitions 2 and 3 to FAT32 because I heard it would make it easier to write to from Ubuntu.
Problem is, since then those partitions won't even appear on the desktop.
They appear in SYSTEM>ADMINISTRATION>DISKS, but it claims they're NTFS.

What's the advice on how to get both Ubuntu and XP to be able to read and write to partitions 2 and 3?

Hopefully this info will help:
> USER@COMPUTER:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865       19454   117194175    f  W95 Ext'd (LBA)
/dev/sda5            4865        9728    39070048+   b  W95 FAT32
/dev/sda6            9729       14592    39070048+   b  W95 FAT32
/dev/sda7           14593       14757     1325331   82  Linux swap / Solaris
/dev/sda8           14758       19454    37728621   83  Linux


---

### Post by jrib on 2006-07-03
Can you post the contents of /etc/fstab?

If you haven't added them there, you should try to do so using this guide: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by Shampyon on 2006-07-03
I won't be able to post up /etc/fstab for a little bit. GRUB's gone missing, and I can't get it back. I tried ome methods I found after searching, but it strangely says the partition I installed to doesn't exist. I tried fixmbr with my XP disk to see if that made a difference to the re-installation of GRUB. Big mistake, it did nothing for me at all.

I'm currently resorting to typing from the liveCD.

*Edit:* I made a new installation of Ubuntu on the second partition just to get GRUB back. I'm gonna look for some way to edit GRUB so that I can delete that second Ubuntu installation without screwing everything up again.

I reformatted the empty partition to ext3. Still can't see it :(

*Edit 2:* I got GRUB working! As always, I've created a brand new problem, though. I've formatted the two spare partitionsas reiserfs, and I can't get them to mount...

---


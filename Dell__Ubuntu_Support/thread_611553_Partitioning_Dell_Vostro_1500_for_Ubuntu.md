---
title: "Partitioning Dell Vostro 1500 for Ubuntu"
date: 2007-11-13
forum: Dell  Ubuntu Support
---

### Post by herold on 2007-11-13
I recently purchased a Dell Vostro 1500, loaded with Windows XP.  My intention is to double-boot it with Ubuntu, preferably 7.10, or maybe Kubuntu 7.10.  I was uneasy about trying to set it up to double-boot with just a Ubuntu or Kubuntu image CD, so I decided to try to shrink the XP partition and make new Linux and Linux swap partitions first with PartedMagic 1.8, which is a live CD based on GParted 0.3.4, and then install the Ubuntu into the partitions that PartedMagic would prepare for it.  I ran PartedMagic, and got the following status of my existing partitions:

Gparted 	/dev/sda	111.79 GiB  

Partition  Filesystem  Mountpoint     Size        Used     Unused    Flags
/dev/sda1  fat16       	/initrd/initrd 101.94 MiB 7.96 MiB 93.98 Mib	 
/dev/sda2  ntfs                              109.18 GiB 9.48 GiB 99.70 GiB boot
unallocated  unallocated                   7.84 MiB   --          --
/dev/sda3  extended                         2.50 GiB   --         --              lba
 /dev/sda5  fat32                               2.50 GiB 735.64 MiB 1.78 GiB

I'm sorry about any folded lines.  I hope you can decipher it.

I am not sure what is the fat16 partition sda1, but I am wondering if it has to do with the Windows restore file, which I assume is the fat32 partition sda5.  I see also that sda1 has a lock symbol; none of the others do.

The PartedMagic instructions say that it doesn't work well (is slow and subject to failure) if a partition that is to be reduced in size is not at the end of the partitions.  It looks to me that the extended partition sda3 (and sda5) will cause a problem here.  I would like to reduce the size of the ntfs partition sda2 down to about 40 GB, and put the extra space into two (or more) partitions in the extended partition, for installing Ubuntu.  So far, I have just looked at the partitions as reported by GParted; I haven't made any changes yet.

Has anyone done this sort of partitioning?  Does it work?  Are there any tricks I should know about, before I mess up my existing partitions?  Is there a better way?

---


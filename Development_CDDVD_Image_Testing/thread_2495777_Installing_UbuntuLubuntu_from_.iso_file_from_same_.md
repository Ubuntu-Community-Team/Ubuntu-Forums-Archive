---
title: "Installing Ubuntu/Lubuntu from .iso file from same hard drive"
date: 2024-03-01
forum: Development CD/DVD Image Testing
---

### Post by scmarko on 2024-03-01
I'm trying to find a solution how to start a Ubuntu installation from an .iso file that is located on LVM on a hard drive. I have a lot of computers with older Ubuntu/Lubuntu versions that should be repartitioned and upgraded to a more recent Ubuntu version.

The hard drive partitioning looks basically like this on the computers:

```
sda                            
+-sda1                         
+-sda2                         
+-sda5                         
  +-ubuntu--vg-root (dm-0)
  +-ubuntu--vg-swap_1 (dm-1)
```

I have tested that I can boot an Ubuntu Live CD .iso file from the LVM hard drive when modifying GRUB2 bootloader, but when trying to repartition the hard drive for a clean installation, it doesn't work. The .iso file has been started with the "toram" parameter in GRUB2. When I try to repartition the hard drive with Gparted (or anything else), I get errors like "Can't deactivate volume group XXXX with XX logical volumes" etc.

So, is it possible to start Ubuntu from .iso file that is on the same partition on the hard drive which I want to repartition? Ubuntu should be loaded completely into RAM and then release any mounts to the hard drive, so a repartitioning and a clean installation of Ubuntu on the hard drive would be possible.

If I place the .iso file on a USB stick, it could probably work then if GRUB2 could start installation from the stick, but I don't have possibility to do that (there are hundreds of computers when old Ubuntu should be upgraded to a new one) and the computers are all in remote locations. So in short I need this:

1. Place .iso file on the LVM partition on the hard drive.
2. Modify grub to load the .iso file when computer boots.
3. From Ubuntu Live running in RAM, repartition hard drive. (this step doesn't work with any Ubuntu version)
4. Install Ubuntu to hard drive from RAM.

If this is possible, what would the place to start customizing the Ubuntu .iso file? I have some experience of customizing Ubuntu .iso files using xorriso and other commands, but is this achievable at all by e.g. modifying init scripts or something else?

---


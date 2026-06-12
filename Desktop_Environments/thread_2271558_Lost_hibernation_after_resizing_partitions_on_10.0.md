---
title: "Lost hibernation after resizing partitions on 10.04"
date: 2015-03-31
forum: Desktop Environments
---

### Post by kakotako on 2015-03-31
Hibernation option has been available at the press of the power button on my netbook running Ubuntu 10.04. I lost it after resizing partitions and I'd like to have it back.

The steps leading up to the loss of the hibernate option:

I made an image of my 32 GB SSD with Clonezilla, replaced the SSD with a 64 GB drive and restored the image to the new drive. After I restored the image the hibernate option was still present and functional.

But, since I cloned a 32 GB drive to a 64 GB drive, the boot partition ended up being smaller than 32 GB and almost half of the drive was unalocated. Using Gparted I deleted the cloned extended and swap partitions, resized the boot partition, and created new extended and swap partitions. In my first attempt I made an error and made the swap partition smaller than my RAM. When I booted in 10.04 I realized the hibernate option was missing.

Then I went back to Gparted, resized the swap partition to more than twice the size of my RAM and the hibernate option was still missing.

```
sudo pm-hibernate
``` shuts down the network, flashes the screen black but then wakes up a split second later without me touching anything. I have a feeling that starting Ubunutu with the swap partition too small for the RAM has reconfigured something.

```
sudo fdisk -l
``` gives:

```
Disk /dev/sda: 63.6 GB, 63612911616 bytes
255 heads, 63 sectors/track, 7733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00073e40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7180    57665536   83  Linux
/dev/sda2            7180        7734     4455424    5  Extended
/dev/sda5            7180        7734     4454400   82  Linux swap / Solaris
```

---

### Post by sudodus on 2015-03-31
I would suggest that you restore the system again from the Clonezilla image. Then you move the extended partition to the end of the drive, and after that grow the root partition to fill the unallocated space after it. (Do not move the head end of the root partition!). See this link (which illustrates a similar situation),

[http://phillw.net/isos/linux-tools/uefi-n-bios/GrowIt.pdf](http://phillw.net/isos/linux-tools/uefi-n-bios/GrowIt.pdf)

---

### Post by v3.xx on 2015-03-31
This has happen to me (and more than once).  Swap does not like to be mess with (move, resize), don't know why that is.

---


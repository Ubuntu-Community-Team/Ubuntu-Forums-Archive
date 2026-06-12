---
title: "device locations switch in RAID array"
date: 2011-03-17
forum: Desktop Environments
---

### Post by orphefs on 2011-03-17
Hi everyone!
I am running Ubuntu 10.10 64.
I have a RAID array consisting of two 1 TB HDD's, controlled by my on-board RAID controller. I have a dual-boot of Ubuntu 10.10 and Windows. The RAID array is mapped in /dev/mapper, and here is the output of *sudo dmraid -ay*

```

RAID set "pdc_dedfhcfdee" already active
RAID set "pdc_dedfhcfdee1" already active
RAID set "pdc_dedfhcfdee2" already active
RAID set "pdc_dedfhcfdee3" already active

```

"pdc_dedfhcfdee1" is the linux *ext4* partition,
"pdc_dedfhcfdee2" is the linux *swap* partition,
"pdc_dedfhcfdee3" is the windows *ntfs* partition.

Note that:

The first HDD device location used to be /dev/sda
The second HDD device location used to be /dev/sdb

However, I recently installed another HDD of 2 TB capacity, outside the RAID array. That worked fine on first boot. However, after I rebooted, 

The first HDD device location became /dev/sdb,
the second HDD device location became /dev/sdc

while the newly installed device became /dev/sda1 ! 

If that wasn't enough, now everytime I connect an external HDD, the device locations change again to something new!

For some reason this really annoys me, since I want the HDD's to appear on the same device locations, no matter how many I have connected! 

By the way, this is the output of */etc/fstab*:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/pdc_dedfhcfdee1 /               ext4    errors=remount-ro 0       1
/dev/mapper/pdc_dedfhcfdee2 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

Any suggestions?

I thought I would ask you guys before experiment, I certainly don't want to mess up my RAID and lose all my data!

Thanks in advance!

---

### Post by orphefs on 2011-03-17
Anyone? :confused:

---

### Post by orphefs on 2011-03-17
Nevermind, I think I solved the problem..Just set the UUID's in fstab, now the drives are mounting in the order I wanted. Still not sure exactly how this worked, but who cares, problem solved :D

---


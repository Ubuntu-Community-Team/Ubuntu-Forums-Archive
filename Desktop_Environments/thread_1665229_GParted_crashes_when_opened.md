---
title: "GParted crashes when opened"
date: 2011-01-12
forum: Desktop Environments
---

### Post by EchoProtocol on 2011-01-12
I'm attempting to format my 80GB hard drive which currently has Windows XP installed. I'm forced to open the trial instead of actually installing Ubuntu, since it freezes and I'm forced to restart. Whenever I try to open GParted, it starts searching for /dev/sdb partitions, then closes about 7 seconds later. Can I fix this or use another program or maybe format the drive on XP instead?

---

### Post by sikander3786 on 2011-01-12
From Applications > Accessories > Terminal, please post the output of this command.

```
sudo fdisk -lu
```

---

### Post by bertszoghy on 2011-02-22
Hello, I am using Ubuntu 10.4 and getting the same, GParted crashes as it opens.

I am trying to remove the partitions from an SD card using a card reader. "It's not happening".

When I do the command "sudo fdisk -lu", I get:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   de  Dell Utility
/dev/sda2   *      208896     1744895      768000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3         1744896   240139619   119197362    7  HPFS/NTFS
/dev/sda4       240140286   488280063   124069889    5  Extended
/dev/sda5       240140288   478111743   118985728   83  Linux
/dev/sda6       478113792   488280063     5083136   82  Linux swap / Solaris

Disk /dev/sdb: 1015 MB, 1015808000 bytes
32 heads, 61 sectors/track, 1016 cylinders, total 1984000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         256     1979647      989696    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 4, 9) logical=(0, 4, 13)
Partition 1 has different physical/logical endings:
     phys=(124, 185, 50) logical=(1014, 5, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2         1979648     1981698        1025+  53  OnTrack DM6 Aux3
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(124, 185, 50) logical=(1014, 5, 16)
Partition 2 has different physical/logical endings:
     phys=(124, 218, 55) logical=(1015, 6, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdb3         1981952     1983999        1024   10  OPUS
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(124, 222, 60) logical=(1015, 11, 2)
Partition 3 has different physical/logical endings:
     phys=(124, 255, 62) logical=(1016, 12, 36)
Partition 3 does not end on cylinder boundary.


When I do the command "gksu gparted", I get:

======================
libparted : 2.2
======================
Backtrace has 16 calls on stack:
  16: /lib/libparted.so.0(ped_assert+0x2a) [0xb76bcf0a]
  15: /lib/libparted.so.0(+0x4258c) [0xb76f458c]
  14: /lib/libparted.so.0(+0x43317) [0xb76f5317]
  13: /lib/libparted.so.0(+0x4460c) [0xb76f660c]
  12: /lib/libparted.so.0(+0xf7b1) [0xb76c17b1]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0xb76c5032]
  10: /lib/libparted.so.0(+0x45fa3) [0xb76f7fa3]
  9: /lib/libparted.so.0(+0x4619f) [0xb76f819f]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0xb76c5e15]
  7: /usr/sbin/gpartedbin() [0x80901e6]
  6: /usr/sbin/gpartedbin() [0x809fc9b]
  5: /usr/sbin/gpartedbin() [0x80c0532]
  4: /usr/lib/libglibmm-2.4.so.1(+0x30eb2) [0xb6eabeb2]
  3: /lib/libglib-2.0.so.0(+0x65def) [0xb6d33def]
  2: /lib/tls/i686/cmov/libpthread.so.0(+0x596e) [0xb6ba496e]
  1: /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb6b12a4e]
Assertion (heads < 256) at ../../../libparted/labels/dos.c:666 in function probe_partition_for_geom() failed.


Any help greatly appreciated.

Bert

---

### Post by sikander3786 on 2011-02-22
Your HDD seems pretty ok to me. It shouldn't cause problems to the partitioner.

Your USB drives has got all sorts of partition errors. If possible, I would recommend to boot an Ubuntu CD and try installation from that. Or if you want to use the USB drive, just delete all the partitions on it and then re-create a startup USB and try again.

---

### Post by bertszoghy on 2011-02-22
Thank you for your response,

I actually was not able to delete the partitions on that SD card from the Ubuntu desktop > right-click on device > format > disk utility > unmount > delete partition

However I was able to delete them on another SD card.

Further, the dubious SD card was reformatted successfully on Windows 7 and I have a Linux electronic board booted and fully working from that very same SD card.

So why is GParted choking?

Cheers,
B

---


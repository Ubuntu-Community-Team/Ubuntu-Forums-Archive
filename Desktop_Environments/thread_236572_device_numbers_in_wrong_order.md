---
title: "device numbers in wrong order"
date: 2006-08-14
forum: Desktop Environments
---

### Post by dguido on 2006-08-14
I've been rearranging my hard drives for the last 2 days and everything works fine now, Ubuntu and Windows both boot and I can access my storage drive just fine.

The problem is that I deleted and combined a bunch of partitions so that a hard drive that used to have:
/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4
has been entirely combined into one partition.  But due to the way I deleted the partitions, I'm left with /dev/sda3 instead of /dev/sda1.

This is what I get if I open up /dev/sda in fdisk and print the partition tables:
```
dan@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 48641.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3               1       48641   390708799   83  Linux

Command (m for help): x

Expert command (m for help): p

Disk /dev/sda: 255 heads, 63 sectors, 48641 cylinders

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 00   0   0    0   0   0    0          0          0 00
 2 00   0   0    0   0   0    0          0          0 00
 3 00   1   5    0 254  63 1023         67  781417598 83
 4 00   0   0    0   0   0    0          0          0 00

Expert command (m for help):

```

Does anyone know how to collapse my partitions so that the one with all my data on it occupies /dev/sda1?

Thanks.

---


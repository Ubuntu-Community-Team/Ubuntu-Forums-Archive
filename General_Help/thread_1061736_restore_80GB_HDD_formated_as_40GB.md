---
title: "restore 80GB HDD formated as 40GB"
date: 2009-02-06
forum: General Help
---

### Post by tommynz1975 on 2009-02-06
Hi folks



I have googled my problem and found adverts. maybe I used the wrong search words.

I have a 80GB but when shipped it was formatted at 40GB
(this model comp got 40GB another got a 80GB HDD)

booting up the system with live Ubuntu cd Gparted reports that the drive is 37GB

installed currently on the system is Ubuntu Hardy. Using the program Disk Usage Analyzer it reports
Total filesystem capacity 72.1GB


many thanks
Tom

---

### Post by hyper_ch on 2009-02-06
post the output of
```

sudo fdisk -l

```

---

### Post by tommynz1975 on 2009-02-06
sudo fdisk -l out put

```
Disk /dev/sda: 40.0 GB, 40019582464 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97899789

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4784    38427448+  83  Linux
/dev/sda2            4785        4865      650632+   5  Extended
/dev/sda5            4785        4865      650601   82  Linux swap / Solaris

Disk /dev/sdb: 4127 MB, 4127195136 bytes
16 heads, 32 sectors/track, 15744 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

```

---

### Post by jerome1232 on 2009-02-06
> **tommynz1975 said:**
> sudo fdisk -l out put

```
[COLOR="Blue"]Disk /dev/sda: 40.0 GB, 40019582464 bytes[/COLOR]
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97899789

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4784    38427448+  83  Linux
/dev/sda2            4785        4865      650632+   5  Extended
/dev/sda5            4785        4865      650601   82  Linux swap / Solaris

Disk /dev/sdb: 4127 MB, 4127195136 bytes
16 heads, 32 sectors/track, 15744 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

```

The disk itself is in fact 40 GB, and your partitions are taking up the entire disk.

---

### Post by tommynz1975 on 2009-02-06
from 
```
sudo lshw
```

 *-disk
                description: ATA Disk
                product: SAMSUNG SP0842N
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BH10
                serial: S0DWJ1TL608468
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=97899789

from
```
sudo fdisk /dev/sda
```
The number of cylinders for this disk is set to 4865.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): 

I chose 'm' from the menu
then I chose 'v'
with the result

7146 unallocated sectors

is this half my HDD not used


Many thanks

Tom

---


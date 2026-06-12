---
title: "Partitioning Help (cfdisk)"
date: 2009-03-10
forum: General Help
---

### Post by thegreenblob on 2009-03-10
Hello, this isn't directly related to ubuntu but I figured someone here could help :P

Basically I wanted to try some new distros so I resized some partitions and made a logical partition to put all my data on that I didn't want to loose. (Used gparted)

And a distro I was trying to install uses cfdisk to partition and I get this error:

```
FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap
                          Press any key to exit cfdisk
```

I've attached a screenshot of a gparted window.

Can anyone help? cfdisk seems to be the only partitioning tool that refuses to load.

Thanks.

---

### Post by meierfra. on 2009-03-10
cfdisk is very picky. It sound like there is a problems with some of the hidden extended partitions. 

Try this:

```
sudo fdisk /dev/sda
w
```

(Here replace /dev/sda by the actual device name of the hard drive in questions.)  This will cause "fdisk" to write the partition table according to its own rules. Maybe that is enough to solve your problem. If not, post the output of

```
sudo sfdisk -d /dev/sda
sudo sfdisk -xluS /dev/sda
```
(again replace /dev/sda by the correct device name)

---

### Post by thegreenblob on 2009-03-10
Thanks for the reply. It seems to still giving me the same error. So here's the output of those commands.

```
joe@desktop:~$ sudo sfdisk -d /dev/sda
[sudo] password for joe: 
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20466747, Id=27
/dev/sda2 : start= 20466810, size=208893195, Id= 6, bootable
/dev/sda3 : start=229360005, size=208893195, Id=83
/dev/sda4 : start=438253200, size=186884145, Id= 5
/dev/sda5 : start=623852208, size=  1285137, Id=82
/dev/sda6 : start=438253326, size=185598819, Id=83
```
```
joe@desktop:~$ sudo sfdisk -xluS /dev/sda

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63  20466809   20466747  27  Unknown
/dev/sda2   *  20466810 229360004  208893195   6  FAT16
/dev/sda3     229360005 438253199  208893195  83  Linux
/dev/sda4     438253200 625137344  186884145   5  Extended

/dev/sda5     623852208 625137344    1285137  82  Linux swap / Solaris
    -         438253201 623852144  185598944   5  Extended
    -         438253200 438253199          0   0  Empty
    -         438253200 438253199          0   0  Empty

/dev/sda6     438253326 623852144  185598819  83  Linux
    -         438253201 438253200          0   0  Empty
    -         438253201 438253200          0   0  Empty
    -         438253201 438253200          0   0  Empty
```

---

### Post by meierfra. on 2009-03-10
The only problem I can see is that partitions are not in the physical order.
So lets see whether fixing the partition  order will solve your problem:


```
sudo fdisk /dev/sda
x
f
w
```

Reboot immediately.

(I'm not sure that this will  solve your problem: I have seen a couple of  posts which claim that "FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap" is a bug in cfdisk which can happen even if  there are no problems with the partition table)

---

### Post by thegreenblob on 2009-03-10
Hmm... still no go. :(

---

### Post by meierfra. on 2009-03-11
Here is one more thing you can try (but I don't have much hope that it will cure the problem)

Download the attached file pt.txt to your desktop. Then in a terminal

```
 sudo sfdisk --no-reread -f /dev/sda < ~/Desktop/pt.txt
```

Reboot and hope for the best.

---

### Post by thegreenblob on 2009-03-12
Tried the above and it didn't seem to work. But I got it to work by deleting all my linux partitions. (Backed up my data on to dvds, and also kind of confused why that worked, but thought it was worth a try :P).

Thanks anyway.

---

### Post by meierfra. on 2009-03-12
> Tried the above and it didn't seem to work.

Oh well. It really seems to be a bug in cfdisk.


> But I got it to work by deleting all my linux partitions.

Great.

> also kind of confused why that worked,

Me too. I might look at the source code of cfdisk and try to figure out how the bug is triggered.

---


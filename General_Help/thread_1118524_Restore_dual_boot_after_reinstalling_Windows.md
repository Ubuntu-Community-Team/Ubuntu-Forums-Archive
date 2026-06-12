---
title: "Restore dual boot after reinstalling Windows"
date: 2009-04-07
forum: General Help
---

### Post by jfwb on 2009-04-07
I currently have Ubuntu and Windows installed and can boot either.  I now need to reinstall Windows which will overwrite the dual boot facility.  Is there any way I can save the current dual boot facility and then restore it after reinstalling Windows?  I don't want to have to reinstall Ubuntu as well.

---

### Post by Usse on 2009-04-07
i always do that:

```
sudo grub
```

check the partition where ubuntu is installed with 
```
find /boot/grub/stage1
```

then, with the output of the previous command, type: (this is an example, you need to change hd0 and 2 with your values) 
```
root (hd0,2)
```

```
setup (hd0)
```

```
quit
```

---

### Post by callie510 on 2009-04-07
hahaha, exactly what the previous poster said ... except two things:

1) the first command is "sudo grub" (not sudo gru :)

2) you will need to boot onto a live CD to do this, fyi.

---

### Post by Usse on 2009-04-07
eheh ops, was a sudo grub ^^ i edited the post. thx for the notice.

---

### Post by jfwb on 2009-06-19
> **Usse said:**
> i always do that:

```
sudo grub
```

check the partition where ubuntu is installed with 
```
find /boot/grub/stage1
```

then, with the output of the previous command, type: (this is an example, you need to change hd0 and 2 with your values) 
```
root (hd0,2)
```

```
setup (hd0)
```

```
quit
```

Thank you for that. I haven't come back until now because I have only noe re-installed WindowsXP. I wnt through the steps you proposed with the following result:

grub>find/boot/grub//stage1
(hd1,2)

grub root (hd1,2)

grub> setup (hd1)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running mbed /boot/grub/e2fs_stage1_5(hd1)"... 17 sectors are 
embedded
succeeded
Running "install /boot/grub/stage1 (hd1)(hd1)1+17p(hd1,2)/boot/grub/stage2/boot/grub/menu.lst"... succeeded
Done

All that looked fine - only problem is nothing has changed and I still don't have dual boot. It just goes straight to Windows.

Did I do something wrong?

---

### Post by merlinus on 2009-06-19
You seem to have more than one hdd.  Run from the live cd, open a terminal and post results of:

```

sudo fdisk -l

```

---

### Post by sundar_ima on 2009-06-19
if you are not comfortable with commands then use Super Grub Disk. Download it from here [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by jfwb on 2009-06-19
> **merlinus said:**
> You seem to have more than one hdd.  Run from the live cd, open a terminal and post results of:

```

sudo fdisk -l

```

Thank you. Quite a long listing but here it is:
&#65279;ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e1a5e1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9689    77826861    7  HPFS/NTFS
/dev/sda2            9690       19456    78453427+   f  W95 Ext'd (LBA)
/dev/sda5            9690       16063    51199123+   6  FAT16
/dev/sda6           16064       19456    27254241    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e785e78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6578    52837753+  83  Linux
/dev/sdb2           19081       19457     3028252+  82  Linux swap / Solaris
/dev/sdb3   *        6579       18703    97394062+  83  Linux
/dev/sdb4           18704       19080     3028252+   5  Extended
/dev/sdb5           18704       19080     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 1048 MB, 1048838144 bytes
32 heads, 63 sectors/track, 1016 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x6c916c91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1015     1023088+   6  FAT16

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1874d9bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sde: 2051 MB, 2051013632 bytes
33 heads, 63 sectors/track, 1926 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        1927     2002927    b  W95 FAT32

Disk /dev/sdf: 8086 MB, 8086618112 bytes
249 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15438 * 512 = 7904256 bytes
Disk identifier: 0x2c6b7369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   ?      125407      245362   925929529+  68  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(116, 100, 32) logical=(125406, 168, 29)
Partition 1 has different physical/logical endings:
     phys=(288, 101, 46) logical=(245361, 67, 59)
Partition 1 does not end on cylinder boundary.
/dev/sdf2   ?       86163      121076   269488144   79  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(357, 32, 43) logical=(86162, 245, 47)
Partition 2 has different physical/logical endings:
     phys=(0, 13, 10) logical=(121075, 74, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdf3   ?       34914      125493   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(34913, 40, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(125492, 109, 49)
Partition 3 does not end on cylinder boundary.
/dev/sdf4   ?       90338       90339       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(90337, 81, 36)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(90338, 176, 44)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by merlinus on 2009-06-20
So which is windows and which is ubuntu?  And is this the booting order in bios?  And what is sdf?

---

### Post by jfwb on 2009-06-25
> **merlinus said:**
> So which is windows and which is ubuntu?  And is this the booting order in bios?  And what is sdf?

Windows is on sda and Ubuntu is on sdb but I am not sure just where. The booting order in bios is floppy drive, dvd drive then hard disk.Other device is enabled (whatever that means).
sdc,d,e are usb drives and sdf is a usb hard drive used for backup purposes.
I hope this information helps and thank you for trying.

---

### Post by merlinus on 2009-06-25
You might try this:

```

sudo grub 
root (hd1,2)
setup (hd0)
quit

```

and restart.

---

### Post by jfwb on 2009-06-25
> **merlinus said:**
> You might try this:

```

sudo grub 
root (hd1,2)
setup (hd0)
quit

```

and restart.

Thank you very much.  That worked just fine.  With the benefit of hindsight, it is of course entirely logical.  What I did before was setup((hd1) which is  not where bios would look when starting up!

I wonder if you would be able to direct me to somewhere which might explain how I could install a different Linux distribution without losing the availability of my present Ubuntu. I get all these disks for different distros with the Linux magazine and it would be interesting to try some of them out.

---


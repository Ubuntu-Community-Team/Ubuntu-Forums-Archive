---
title: "gparted not seeing partition table-- ubuntu 8.04, 8.10, and 9.04"
date: 2009-04-08
forum: General Help
---

### Post by AFarris01 on 2009-04-08
PROBLEM! of course...

The problem is that my brother's computer has been messed up graphically for a while, and we were trying to re-install so he could just start with a clean, happy system... unfortunately, things aren't working out that way right now.

the problem is that during the installation step when you get to format your partitions, the partition editor does not see his current partition table, despite the fact that the partitions can still be seen and mounted from the 'Computer' view and elsewhere.

I also tried launching gparted manually (i.e. not during the install, but still in the Live environment) but still no joy... gparted doesnt see the table either.

I've examined the computer using live CDs from 8.04, 8.10, and 9.04, as well as the alternate install disks, but the partitions cant be viewed in any of them.

This issue is new to me, because I've installed ubuntu on the system before (obviously), from a 8.04 disk, and it saw the previous partition table just fine.

gparted running from inside the existing install DOES see all the partitions properly, but this doesn't help because he has several partitions, and i only want to wipe one of them.

his current partition is set up like so:
   20GB EXT3 (linux system) *this is the one i want to wipe
   130GB EXT3 (linux home) *wanna keep this one
   8GB swap (dont care)
   342GB NTFS (general shared storage) *also keep

Any ideas?? I really appreciate any help on this one...it's got me stumped ](*,)

---

### Post by meierfra. on 2009-04-08
Post the output of

```
sudo fdisk -lu
sudo sfdisk -d 
```

---

### Post by utnubuuser on 2009-04-08
Hi - have you tried downloading and burning a copy of gparted from sourceforge.net?

I've come across a similar situation from time to time, and the only "fix" I found was to use a gparted liveCD.

---

### Post by AFarris01 on 2009-04-09
Thanks for the posts so far!

@meierfra
I can't access the PC right now, so i cant get the output of the given commands yet...stand by...

@utnubuuser
I dont know if using a gparted liveCD would help, since the issue is that the installer cant tell the difference between my partitions, so i can't pick the correct one to install to, and i doubt using a gparted liveCD to wipe the desired partition would do anything to fix that issue...It's still worth trying tho, so i'll start that download right away!

I appreciate the help guys! i'll post back as soon as i get that output!

---

### Post by AFarris01 on 2009-04-09
OK, i've got the desired output here...

$ sudo fdisk -lu 
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x17151714

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   681043544   340521741    7  HPFS/NTFS
/dev/sda2       681043545   976768064   147862260    f  W95 Ext'd (LBA)
/dev/sda3       943192278   959964074     8385898+   7  HPFS/NTFS
/dev/sda5       681043671   903190364   111073347   83  Linux
/dev/sda6       903190428   943192214    20000893+  83  Linux
/dev/sda7       959964138   976768064     8401963+  82  Linux swap / Solaris

$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=681043482, Id= 7, bootable
/dev/sda2 : start=681043545, size=295724520, Id= f
/dev/sda3 : start=943192278, size= 16771797, Id= 7
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=681043671, size=222146694, Id=83
/dev/sda6 : start=903190428, size= 40001787, Id=83
/dev/sda7 : start=959964138, size= 16803927, Id=82

---

### Post by meierfra. on 2009-04-09
The partition table is slightly corrupted.  There is a bogus entry in the partition table

> omitting empty partition (5)


and the primary partition /dev/sda3

> /dev/sda3 943192278 959964074 8385898+ 7 HPFS/NTFS

sits inside the extended partition /dev/sda2:

> /dev/sda2 681043545 976768064 147862260 f W95 Ext'd (LBA)

To fix the partition table, download the attached file PT.txt to the Ubuntu Desktop. Then open a terminal and type


```
sudo sfdisk -f --no-reread /dev/sda < ~/Desktop/PT.txt
```


The next step is only necessary, if you still want to boot  the computer before you reinstall:

```
sudo grub
```
and at the "grub>" prompt:

```
root (hd0,5)
setup (hd0)
quit
```

---

### Post by AFarris01 on 2009-04-10
meierfra:

Thanks so much for that, It worked like a charm! My brother is now running a 9.04beta install, and loving it.

Thanks a bundle!

---

### Post by meierfra. on 2009-04-10
> Thanks so much for that. It worked like a charm! 

Great.  Glad to be of help.

---

### Post by crewkid89 on 2009-09-29
Hi everyone sorry to resurrect a thread but I've got a similar problem.  I tried using the method prescribed here (modified to my partition table) but it was a no go. Here are the read outs of those two commands.

kevin@kevin-desktop:~$ sudo fdisk -lu
[sudo] password for kevin: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    97659134    48829536    7  HPFS/NTFS
/dev/sda2        97659135   156248189    29294527+   5  Extended
/dev/sda3       113290443   121290749     4000153+  82  Linux swap / Solaris
/dev/sda5        97659261   113290379     7815559+  83  Linux
/dev/sda6       121290813   156248189    17478688+  83  Linux

kevin@kevin-desktop:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 97659072, Id= 7, bootable
/dev/sda2 : start= 97659135, size= 58589055, Id= 5
/dev/sda3 : start=113290443, size=  8000307, Id=82
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 97659261, size= 15631119, Id=83
/dev/sda6 : start=121290813, size= 34957377, Id=83

Any ideas?  I need to do a fresh install but I don't want to lose my /home partition or my windows partition (It's got all my games).

Thank you

---

### Post by tubia87 on 2010-05-19
Hi all,
I have the same problem.
I have 2 disks: sda:500 gigabyte and sdb 1,5 terabyte. sdb has 2 partitions: 1 ext4 empty, only for data and the other in wich I installed Xp. In sda I (should) have 5 partitions: 1 with ubuntu 10.04 beta2, 1 with the /home, 1 is an NTFS partition with data, 1 with linux mint (that I have to erase) and 1 with linux swap.
sda is now lost. This happened after I installed xp then, booting from liveCD and opening GParted, sda was all unallocated. I executed fdisk on /dev/sda and thi is the result:
```

ubuntu@ubuntu:~$ sudo fdisk /dev/sda
omitting empty partition (5)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): p

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe541e541

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5159    41432617+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2            5159       60801   446949921+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3   *       10459       57425   377262427+   7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda5            5159       10458    42569773   83  Linux
/dev/sda6           57426       60752    26724096   83  Linux
/dev/sda7           60753       60801      393561   82  Linux swap / Solaris
```
I see that my situation is similare to this one.
Running testdisk, this is what I got in the last screen:
```

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   1  1  5158 254 63   82879272
P Linux                 5158  78 41 10457 254 63   85139546
P HPFS - NTFS          10458   0  1 57424 254 63  754524855
L Linux                57425   1  1 60751 254 63   53448192
L Linux Swap           60752   1  1 60800 254 63     787122


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock, 43 GB / 40 GiB
```
First disk is ubuntu 10.04 beta2
Second disk is the /home partition
Third disk is the NTFS data partition (that in the beginning was set as *=Primary bootable)
Fourth disk is linux mint
Fifth disk is linux swap

Testdisk doesn't let me to hold both the first and the second partition: one of the two should be deleted (in other cases it says that the structure is bad)

Any hints or suggestions about what I should do whould be really appreciated.

Thank you in advance.

P.s.: Tell me if I have to open another thread in order to discuss this issue.

---


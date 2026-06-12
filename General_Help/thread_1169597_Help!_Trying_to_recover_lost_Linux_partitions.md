---
title: "Help! Trying to recover lost Linux partitions"
date: 2009-05-25
forum: General Help
---

### Post by HotForLinux on 2009-05-25
After using an Ubuntu Live CD I have lost the Linux partitions in a system with valuable data and without backup. I ignore whether the problem lies in the MBR, boot sectors, an inode, the whole file system or if the data has been lost. I'm not shure if Grub's **setup** command or other commands will worsen the situation so I need help on:

A) How to Backup before attempting to repair the partitions?
B) How to make a complete or a step by step diagnosis? (instead of trial and error with repairing commands)
C) If it is possible, how to repair the disks?

What I want is to be able to mount the partitions so that I can backup the important directories in the Linux partitions.

--------------- The Story: -----------------
I had been experiencing random freezes due to hardware problems in a compatible PC with dual boot.
While trying to determine whether it was the RAM, the processor, the motherboard or other components, it experienced a number of crashes. Each time more often. In the end it was impossible to boot from either system nor from a Xubuntu live CD and rarely from an Ubuntu Live CD for a few minutes. But never happened anything near to what has happened now.

A  few days ago I decided to change the processor. After doing so, I could boot perfectly well from all Live CD's.
So I installed the two Hard Drives (with the dual boot) and booted the Linux system without problems and logged in, but after several minutes, the system crashed (it freezed). Later, I tried the same choosing the Windoze option in the GRUB menu but the system also freezed.

I wanted to explore the file systems before extracting the stored data, so I booted with an Ubuntu Live CD (Hardy). To do so, I mounted the partitions just by choosing the corresponding options in the "Places" Menu. The system mounted all partitions rw. But due to group restrictions and to be able to explore one of them I created a group in the live system and added the user ubuntu to it. Everything went ok until I logged out. When logging out, the system outputted some lines on the terminal and then seemed to be caught in a loop without making any progress so I turned the power off.

The big surprise came when I booted again from the hard disks and, instead of the GRUB menu, I read:

[FONT=Courier New]Searching for boot record from IDE-1 ..OK

GRUB Loading Stage 1.5.

GRUB loading, please wait...

Error 17[/FONT]

--------------- Some Information: -----------------

If I boot from the Ubuntu Live CD I can access (mount) the Windoze partitions ONLY, and I can query **fdisk** which gives me the correct information of the partitions as they were before this problem started:


```
$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29512950

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69737369

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2797    22466871    7  HPFS/NTFS
/dev/sdb2            2798        2979     1461915   82  Linux swap / Solaris
/dev/sdb3   *        2980        4073     8787555   83  Linux
/dev/sdb4            4074        4865     6361740   83  Linux


$ cat /proc/partitions

major minor  #blocks  name

   8     0   39082680 sda
   8     1   39070048 sda1
   8    16   39082680 sdb
   8    17   22466871 sdb1
   8    18    1461915 sdb2
   8    19    8787555 sdb3
   8    20    6361740 sdb4
   7     0     690060 loop0
```------------------------------

If I boot from a Floppy with GRUB installed in it, the command "**root**" returns the following error messages: 

[FONT=Courier New]root (hd0,0) ----> Filesystem type unknown, partition type 0x7
root (hd1,0) ----> Filesystem type unknown, partition type 0x7
root (hd1,1) ----> Filesystem type unknown, partition type 0x82
root (hd1,2) ----> Filesystem type unknown, partition type 0x83
root (hd1,3) ---->  Filesystem type unknown, partition type 0x83

for any other values for x and y:
root (hdx,y) ----> Error 22: No such partition [/FONT] 


Also, The commands **kernel** and **configfile** together with their parameters to boot return:
[FONT=Courier New]
Error 17: cannot mount selected partition.[/FONT]

---

### Post by VMC on 2009-05-25
Try using testdisk to analyse the situation first.

I don't know if you have a spare HD, but Clonezilla will image any partition and/or hard drive.

From grub disk, this doesn't reveal anything, "grub> find /boot/grub/stage1"?

---

### Post by HotForLinux on 2009-05-25
For the first backup:

- It would be difficult for me to find another hard drive. I already need an extra one for the backup.
I can boot from a live CD to access those hard disks and  I can use a laptop in the LAN although I don't think this can be useful.

- Clonezilla is not on the repository. Is it possible to use it with the limitation mentioned above?. I'll search for it, but it seems strange that there isn't a tool for that purpose on the repository. Can't the command **dd** be used for the same purpose?

- Telling the copy of GRUB installed on the floppy: "**find /boot/grub/stage1**" or "**find /boot/grub/stage2**" returns

Error 15: File not found

But I think that it searches in the floppy only.


Also:
```
grub>root (hd1)
Filesystem type unknown, using whole disk
 
grub>find /boot/grub/stage1
Error 15: File not found
```same thing with (hd0) and stage2 and their combinations.


```
grub>root (hd1,2)
 Filesystem type unknown, partition type 0x83
 
grub>find /boot/grub/stage1
Error 15: File not found
```Here too, It seems to be searching in the floppy only.

---

### Post by VMC on 2009-05-25
The grub boot floppy will search the hard drive. Since you can't mount the Linux file system, do you remember what file system type use used? Ext2,3,4 or something else?

If by chance it is Ext4, then that floppy disk won't work. Get the lastest Super Grub Disk, get to the grub prompt and type the find command.

Sorry, but [Clonezilla]("http://www.clonezilla.org/") is a separate mini distro disk.

It has a rather odd interface, but just follow the instructions.

---

### Post by HotForLinux on 2009-05-25
There was no ext4 partition. The partition are/were ext2 and ext 3 .
As I explained before, **fdisk -l** still returns correctly the information of the partitions on both drives.


I'm going to study Godzilla and **testdisk** and see what I can do. The problem is that by now I've only got the live CD and a laptop in the LAN to solve this.

It would be great to try and find the solution with these means first.

If that's not possible then I'll think whether to buy a unit to convert those  HDs into external USB drives that I can plug into the laptop and examine them or to find a HD where to do the backup and install a system there too in order to work on that PC, which I still ignore if it works properly with the HD drives, since I haven't determined the reason for the last two crashes: on one disk with windoze and on the other with Linux.

---

### Post by HotForLinux on 2009-05-26
I think that the partition table is ok but that the linux filesystems are corrupted.
The crash affected the way the filesystem annotations ought to be carried out. Therefore I should have rebooted with the same system (or a Read Only one) so that the journalling system would have repaired the filesystem. But since I booted with the Ubuntu live CD and explored the HD filesystems in RW-mode, the filesystems must have been modified without the needed previous fix during boot time.

Don't you think so?

---


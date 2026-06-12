---
title: "Ubuntu installation failed, did not produce partitioning window"
date: 2009-03-12
forum: General Help
---

### Post by boothruwindow on 2009-03-12
I just tried to install Ubuntu 8.1 on a two-drive Acer. When I got to Step 4, there was nothing but blank space in the uneditable text box where something apparently should have been listed, disabled buttons. The only options I had were to press the Quit, Back, or Forward buttons at the bottom, so I pressed Forward. The error message was 

[FONT="Courier New"]
"No root file system is defined.
Please correct this from the partitioning menu."[/FONT]

Well, I thought it was supposed to be taking me to that menu, so there's something wrong. 

I'll never know for sure what went wrong, perhaps I left the 2nd hard drive as unallocated space, instead of creating a new partition on it while trying to redefine my partitions through Vista (and then wouldn't you think that Ubuntu could handle the creation of it's own partitions). What I do know is that (in a prior installation attempt) the Ubuntu installer started treating my entire 2nd hard drive (where I intended to install Ubuntu) as "Free Space" and, under the Guided mode of the partitioning window, chose to cut into my Vista partition instead of use that free space! I tried to correct this under Manual, but it would not allow me to expand anything into this space - therefore, the only choice I had at that point was to go with Ubuntu's Guided choice, while hoping it would'nt be too destructive. The results were disasterous - the installation aborted, and now I can't even boot into Vista (no great loss if I can replace it with something which works). Instead of a dual boot screen when I power up, there's a GRUB Error 22.  I now have to run OS from the Ubuntu CD, and at least that will boot and run, but it can't define it's own root file system to install on - why is that?

Thanks.

---

### Post by ajgreeny on 2009-03-12
Let's start by finding what is on your computer.  Using the live CD, open a terminal and run the command ```
sudo fdisk -l
```which will produce some output with your current partitions listed on both hard disks.  You can then look at what %age is used on the disks with System >Administration > Partition editor.  All partitions will be shown with a more graphical display of usage etc etc.

Come back with what you find and we should be able to tell you the next step.

---

### Post by boothruwindow on 2009-03-12
> **ajgreeny said:**
> Let's start by finding what is on your computer.  Using the live CD, open a terminal and run the command ```
sudo fdisk -l
```which will produce some output with your current partitions listed on both hard disks.  You can then look at what %age is used on the disks with System >Administration > Partition editor.  All partitions will be shown with a more graphical display of usage etc etc.

Come back with what you find and we should be able to tell you the next step.

[COLOR="Navy"]Sorry I couldn't respond sooner, had to go to work and I'm not wired in. Here's the fdisk output:[/COLOR]

[FONT="Courier New"][B]ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
[/B][/FONT]

---

### Post by boothruwindow on 2009-03-12
Oops, now I think you meant the letter, "-l", not "1"!

Here is the output for sudo fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0e4765c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       31055   239215882+   6  FAT16
/dev/sda3           31056       31447     3148740    7  HPFS/NTFS

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         976     7839698    b  W95 FAT32

---

### Post by Locutus_of_Borg on 2009-03-12
I encountered this exact situation installing crunchbang which uses the same installer

turns out this is a result of having a partition mounted

if running ```
sudo su
umount -a
ubiquity
``` 
does not fix it, then i dont know

---

### Post by boothruwindow on 2009-03-14
That worked - thanks!

---

### Post by nrama on 2009-03-15
I am not certain if this is the correct place to air this problem

I have a dual boot system running Ubuntu 8.04 and Mandriva 2008.1. After a number of operations,too numerous to enumerate I have ended up with the following situation,It all started with an attempt to fix a chronic problem of error 18 after about 30 or so reboots. . When I boot into Ubuntu and go into partition editor (gparted) I get a dismal gray bar with "unallocated 74.53 GiB".Using the live Disk is no better.Booting into Mandriva, the control center shows the disk partition information clearly as expected with the entire disk partitioned  per fdisk -l as follows;

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2449    19671561   83  Linux
/dev/sda2            2450        7850    43383532+  83  Linux
/dev/sda3            7851        8215     2931862+  82  Linux swap / Solaris
/dev/sda4            8216        9730    12169237+   f  W95 Ext'd (LBA)
/dev/sda5            8216        8767     4433908+  83  Linux
/dev/sda6            8768        8896     1036161   82  Linux swap / Solaris
/dev/sda7            8897        9729     6691041   83  Linux

Sda1,2, & 3 are used by Ubuntu and the rest by Mandriva
I have tried everything I can think of short of reinstalling and destroying the existing partition table,which I am loath to do.

The computer works perfectly in all other respects under both the OSes. I shall be grateful for any pointers to resolve this niggly problem.

---


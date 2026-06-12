---
title: "Inspiron 1520 : 10.10 hangs at preparing installation screen"
date: 2010-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dudeover on 2010-12-16
As described in the title, I am trying to install Ubuntu 10.10 from a USB pendrive on my Dell Inspiron 1520 that actually runs two other versions of Ubuntu. I can boot from the pendrive without any problem. The problem is that I cant go pass the second screen "Preparing to install Ubuntu" . When I click on "next" on these screen, it hangs for eternity (more than an hour at least). Maybe it will help, I can't run gparted neither, but everything else on the liveUSB is working fine. I succeed to install my wifi drivers for instance (but not for all installations tries).
So, I think I need some help!
Jay

---

### Post by mhosseina on 2010-12-25
I have exactly the same problem
everything on live cd works fine but gparted and installation holds on preparing to install for ever.

My system spec is:

Toshiba U300

160GB hard disk
3G RAM
2.4 GHz Core 2 Due

---

### Post by awtprod on 2010-12-27
bump. Having the same issue with my Dell Inspiron 1525. I'm trying 10.04 but not having much luck with that either.

---

### Post by mikkomfg on 2010-12-27
Having the same problem with my Fujitsu Lifebook P3110. It just doesn't get anywhere even I leave it there for hours. When I kill the process it 
usually just kills it and I can try installing again but one time I got this:
"Sorry, the package "linux-image-2.6.35-24-generic 2.6.35-24.42" failed to install or upgrade."
Tried using both live and netbook versions. 

Got it working. It for some reason wants to have all usb ports clear. As installing from usb stick you can't do that. So it stalls. I tried and it did the same with 10.04. Then I tried 9.04 which worked. Awful lot of a trouble to go through 9.04->9.10>10.04->10.04 but heck, it works.

---

### Post by Ausmosis on 2010-12-29
Same problem here but on a HP Compaq NC8000 laptop. I used a CD and tried a fresh install but it hangs at the "Preparing to install Ubuntu" screen when I click the forward button.

---

### Post by Oamey on 2010-12-29
Same thing's happening on my XPS 400...

Used same usb install on my optiplex and it installs fine.

---

### Post by Oamey on 2010-12-29
Alright, I tried installing 10.04 and it hung on the part where it was scanning the disks/hardware. I unplugged my internal CDRW drive, rebooted, tried again, and it installed fine. Weird.

---

### Post by ground21 on 2010-12-31
Same problem on ThinkPad T61 with WD Scorpio Blue 320GB.
I've tried disconnecting USB mouse and internal dvd drive. 

**this is sudo parted -l output:**
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD3200BEVT-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  64.4GB  64.4GB  primary   ntfs            boot
 2      64.4GB  85.9GB  21.5GB  primary   ext4
 3      85.9GB  90.2GB  4294MB  primary   linux-swap(v1)
 4      90.2GB  320GB   230GB   extended
 5      90.2GB  320GB   230GB   logical   ntfs


Backtrace has 15 calls on stack:
  15: /lib/libparted.so.0(ped_assert+0x31) [0x7f68672d75c1]
  14: /lib/libparted.so.0(+0x392f6) [0x7f68673022f6]
  13: /lib/libparted.so.0(+0x39a73) [0x7f6867302a73]
  12: /lib/libparted.so.0(+0x3a72d) [0x7f686730372d]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x1cb) [0x7f68672ddd3b]
  10: /lib/libparted.so.0(+0x3bc74) [0x7f6867304c74]
  9: /lib/libparted.so.0(+0x3be65) [0x7f6867304e65]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0x7f68672de815]
  7: parted() [0x40698e]
  6: parted() [0x40778d]
  5: parted() [0x4097d4]
  4: parted() [0x40a9cf]
  3: parted(main+0x2c) [0x40aadc]
  2: /lib/libc.so.6(__libc_start_main+0xfe) [0x7f6866adfd8e]
  1: parted() [0x404fa9]
                                                                          

You found a bug in GNU Parted! Here's what you have to do:

Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:

Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:

    http://ftp.gnu.org/gnu/parted/

Please check this version prior to bug reporting.

If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:

    http://www.gnu.org/software/parted

for further information.

Your report should contain the version of this release (2.3)
along with the error message below, the output of

    parted DEVICE unit co print unit s print

and the following history of commands you entered.
Also include any additional information about your setup you
consider important.

Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:662 in function
probe_partition_for_geom() failed.

Aborted (core dumped)

```

**sudo fdisk -l output:**

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002f2d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7833    62918541    7  HPFS/NTFS
/dev/sda2            7834       10444    20972857+  83  Linux
/dev/sda3           10445       10966     4192965   82  Linux swap / Solaris
/dev/sda4           10967       38913   224484277+   5  Extended
/dev/sda5           10967       38913   224484246    7  HPFS/NTFS

Disk /dev/sdb: 4005 MB, 4005560320 bytes
21 heads, 21 sectors/track, 17740 cylinders
Units = cylinders of 441 * 512 = 225792 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          19       17741     3907648    c  W95 FAT32 (LBA)

```

[B]IMPORTATNT:
Problem above occured using USB pendrive (4gb patriot). 
I've burned DVD (from CD image) and now I able tu run installation process.[/B]

---

### Post by tofu-lion91 on 2011-01-17
I'm having the same problem. Trying to install Ubuntu 10.10 Netbook on a Dell Mini 10 already running Win7 and it just keeps hanging at the "Preparing to install Ubuntu-Netbook" screen when I click Forward.

Tried using 2 different flash drives but it's not working.

Any ideas? :S

---

### Post by zeating on 2011-01-18
Same problem

---

### Post by tofu-lion91 on 2011-01-18
Well I've found an alternative but I think it'd only work if you're dual booting.

I downloaded the iso and daemon tools on the netbook (in Win7), mounted the disk image and it let me install Linux within Windows.

Seems fine so far :)

---

### Post by cyberwizzard on 2011-02-01
FYI: the dump from parted shows that libparted crashes. While running 'apt-get install gparted' solved the crash under 'parted' for me, it looks like 'parted_server' is part of 'ubiquity' which still crashes.

As it lists my hard drive just fine, I'm now burning a DVD to see if removing the USB drive from the equation solves things.

Edit: My DVD drive died in the 3+ years I did not use it.

However, I did manage to fix the issue as I found stories about corrupt partition tables. I attempted to remove the FAT32 partition on my Imation USB drive but that didn't work: the installer crashed and so did 'gparted' on my Gentoo system.

**BIG FAT WARNING: The following operation erases the partition table on the designated drive. If you enter the wrong device name, you will end up REMOVING ALL DATA on the target drive.**

That being said, I have a single SATA device in my computer, which is called 'sda' and my Imation USB drive is called 'sdb'. Begin by unmounting the USB drive if it is still mounted. Next erase the partition table by zeroing the first 512 bytes of the device:
```
dd if=/dev/zero of=/dev/sdb bs=512 count=1
```
In this command, '/dev/zero' contains an unlimited amount of bytes with the zero value, '/dev/sdb' points to the USB drive (**Make sure this matches the device name of your USB device**). And the other 2 arguments tell 'dd' to copy 512 bytes. Note that the target is 'sdb', not 'sdb1' which would insert the zero bytes in the first partition, which is not the same as erasing the partition table.

Next, use 'fdisk' to create the partition table again:
```
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x6e3ce960.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4, default 1): 
Using default value 1
First sector (2048-7823359, default 2048): 
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-7823359, default 7823359): 
Using default value 7823359

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): b
hanged system type of partition 1 to b (W95 FAT32)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.
```

Now create the FAT32 filesystem again (note that I've named the drive "Imation"):
```
mkfs.vfat -n "Imation" /dev/sdb1
```

Done. At this point, running 'parted' or 'gparted' should prove that the USB drive no longer crashes the partitioning libraries. Reinstall Ubuntu on the stick (for example using unetbootin) and install.

---

### Post by mitchmao on 2011-02-03
Bump.

---

### Post by Ivanovich78 on 2011-02-12
I was having the same issue here.

Changing the pen drive I was using for the installation have worked for me, buddies :)

I was installing using a 4GB EMTEC pen drive, and trying the same thing with my old 1GB EMTEC pen drive did the trick.

Hopefully this may work for you too.

---

### Post by j4m355 on 2011-09-25
this worked for me (when installing from pen drive):

click proceed, quickly remove pen drive, when the screen advances put the pen drive back in

---


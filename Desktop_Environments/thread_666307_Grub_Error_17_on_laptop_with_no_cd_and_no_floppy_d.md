---
title: "Grub Error 17 on laptop with no cd and no floppy disk"
date: 2008-01-13
forum: Desktop Environments
---

### Post by hazla on 2008-01-13
My PC: Laptop Asus s5n (no cd, no floppy disk)
OS: dualboot: Ubuntu 7.06 (or 7.10 - can't remember) and WinXP

I am a newbie. 
A few month ago, I formated my laptop and installed Ubuntu and WinXP in dualboot. This was my first experience with linux and everything ran OK.
Unfortunately, I don't use this computer on a regular basis and I forgot my password. A friend of mine tried to change the password and now I obtain the Grub error 17.

I don't have external floppy disk drive.
I can't install external cd drive without floppy disk drive.
So I tried to make a Super Grub Disk USB Flash Drive.

I installed Unbuntu 7.10 in a friend's PC (already have WinXP so dualboot) and follow instructions I grabbed around. Remember: I am a Newbie. All of this sound to me like incantations. I don't now what I am doing!

I've downloaded super_grub_disk_english_usb_0.9673.tar.bz2 form forjamari

I click on the archive: it opens the Archive manager
I extract the files to the USB Flash Drive.
Now, I have a folder named "boot" on my USB Flash Drive

I tried to identify my USB Flash Drive (256MB)
-----------------------------------------------------------------------
$ sudo fdisk -l

get this:
-------------------------------------------------------------------
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f0c043a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       57515   359590927+   f  W95 Ext'd (LBA)
/dev/sda3           57516       60801    26394795   83  Linux
/dev/sda5           12749       57367   358402086    e  W95 FAT16 (LBA)
/dev/sda6           57368       57515     1188778+  82  Linux swap / Solaris

Disk /dev/sdb: 256 MB, 256901120 bytes
255 heads, 63 sectors/track, 31 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000531b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          31      247983+   6  FAT16
-----------------------------------------------------------------------------------------
OK. so, the name of the device is: /dev/sdb

Now I am going to the Grub menu or something:
--------------------------------------------------------------------------
$ sudo grub

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub >
----------------------------------------------------------------------------

I Check the other name of the drive (I don't now why there is two name: /dev/sdb and hd1)
-----------------------------------------------------------------------------
grub> geometry (hd
-------------------------------------------------------------------------
press Tab and get:
---------------------------------------------------------------
 Possible disks are:  hd0 hd1
--------------------------------------------------------------

I check the first one: hd0 and get:
-----------------------------------------------------------------
grub> geometry (hd0)
drive 0x80: C/H/S = 60801/255/63, The number of sectors = 976773168, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0xe
   Partition num: 5,  Filesystem type unknown, partition type 0x82
---------------------------------------------------------------------------------------------
OK, hd0 is the 500Gb drive
I check the other one: hd1 and get:
---------------------------------------------------------------------
grub> geometry (hd1)
drive 0x81: C/H/S = 31/255/63, The number of sectors = 501760, /dev/sdb
   Partition num: 0,  Filesystem type is fat, partition type 0x6
---------------------------------------------------------------------
OK, hd1 is my Usb Drive.

Now I can try to build the Super Grub Disk USB Flash Drive:
---------------------------------------------------------------------
grub> device (hd1) /dev/sdb

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/fat_stage1_5" exists... yes
 Running "embed /boot/grub/fat_stage1_5 (hd1)"...  23 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+23 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> quit 
$ sync
------------------------------------------------------------------------------

It seems I've done OK!
So let's test the Super Grub Disk USB.

I restart the PC with the USB drive as default boot and nothing happen:

On the PC that working, I get the normal dualboot menu.
On my laptop: the same Grub Error 17.

What am I doing wrong?

---

### Post by adrian15 on 2008-01-16
> **hazla said:**
> 
It seems I've done OK!
So let's test the Super Grub Disk USB.

I restart the PC with the USB drive as default boot and nothing happen:

On the PC that working, I get the normal dualboot menu.
On my laptop: the same Grub Error 17.

What am I doing wrong?

If you are in Linux and you cannot boot it from qemu.

qemu -boot c -hda /dev/sdb

then you should try to install it with super grub disk own grub.

You download super grub disk source code.
You untar it.
You go to dev_grub folder. You run: ./update_grub_binaries.sh .
You go to dev_grub/grub/ and you run ./grub .

Do not miss the ./ !

Inside ./grub run the commands you already know and try to see if the usb boots.

Sometimes the usb is built ok with SGD's own grub, sometimes in ubuntu systems, sometimes in debian systems, sometimes in fedora systems, sometimes is not built ok.  And I do not know why! :oops:

If you can boot it from qemu then it's a probably a bios/pendrive compatibility problem.

Any doubt just ask. (I am not as good as Herman at explaining. ;) )

adrian15

---

### Post by hazla on 2008-01-22
Thank you for your reply and sorry for the delay. I was supposed to receive an email to alert me, I did not.

I tried to boot the USB pen with qemu and it works.

But the interesting thing is that I discover that I have made a confusion when testing on the working PC. The Grub's first screen is very similar to a normal boot from the hd. I though it did not work but in fact it did. Sorry for that.

So, my problem is make it work on my asus s5n Laptop.

Any idea?
Thank you.

---

### Post by hazla on 2008-01-22
Maybe better I start a new thread on the laptop section.

---


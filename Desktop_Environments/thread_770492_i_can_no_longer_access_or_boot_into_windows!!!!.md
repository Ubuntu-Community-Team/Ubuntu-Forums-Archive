---
title: "i can no longer access or boot into windows!!!!"
date: 2008-04-27
forum: Desktop Environments
---

### Post by gobbledigook on 2008-04-27
Hi everyone!

bit of a noob round here so please go easy on me:)

Yesterday i installed ubuntu 8, i had to manually edit the partitions as i have 5 hard disks - 3 sata and 1 ide, my windows drive is a sata and was plugged into sata2 on my motherboard so it was not the default drive for the partition tool to auto edit during install.

so i reduced the windows partition and set up an ext filesystem and a swap area, installed ubuntu with no further errors.

However grub didn't pick up the windows partition and when i manually edited it to point toward where the windows partition should be it has "Error 12: invalid device requested" i was a bit upset about this obviously as i can no longer boot into windows!!! i have unplugged all other drives except the main drive and plugged it into sata1 on the motherboard, so now i can boot into Ubuntu no problems but still no windows!

ok i ran the windows install disk and went to recovery mode, the diskpart tool there gave me this:
[PHP]
-:partition1 (windowsxp fault tolera)
c:partition2
f:partition3[/PHP]

chkdsk sais "volume appears to contain one or more unrecoverable problems"

and fixboot gives BSOD!!

then, i boot into ubuntu and run the following disk looky at type commands i've picked out of other posts:

[PHP]dan@dans-ubuntu:~$ sudo fdisk -l
[sudo] password for dan: 

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa135fb71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+  86  NTFS volume set
/dev/sda2            4865        9964    40965750    5  Extended
/dev/sda5            4865        9749    39238731   83  Linux
/dev/sda6            9750        9964     1726956   82  Linux swap / Solaris
dan@dans-ubuntu:~$ [/PHP]

[PHP]dan@dans-ubuntu:~$ sudo fdisk -u /dev/sda1

Command (m for help): m
Command action
   a   select bootable partition
   b   edit bootfile entry
   c   select SGI swap partition
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit

Command (m for help): v
Unused gap of 218125413 sectors - sectors     4096-218129508
The Partition 1 and 2 overlap by 1191069742 sectors.

The swap partition has no swap type.

Command (m for help): p

Disk /dev/sda1 (SGI disk label): 255 heads, 63 sectors, 4863 cylinders
Units = sectors of 1 * 512 bytes

----- partitions -----
Pt#     Device  Info     Start       End   Sectors  Id  System
 1: /dev/sda1p1  boot 218129509 1920119918 1701990410   7  SGI efs
 2: /dev/sda1p2  swap 729050177 1273024900 543974724  74  Unknown
 9: /dev/sda1p3               0      4095      4096   0  SGI volhdr
11: /dev/sda1p4               0  78124094  78124095   6  SGI volume
----- Bootinfo -----
Bootfile: /unix
----- Directory Entries -----

Command (m for help): [/PHP]

Gparted shows the first partition as having an unknown filesystem and the partition is inaccssable through ubuntu either?!? it is unable to mount:
[PHP]
dan@dans-ubuntu:~$ sudo mount /dev/sda1
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
dan@dans-ubuntu:~$[/PHP]

i really am not sure what i can do about this? i don't really understand all this output but from what i can gather somehow the disk label for partition 1 is corrupted? or missing?

any and all opinions and ideas encouraged:)

thanx! dan

---

### Post by gobbledigook on 2008-04-27
any ideas?

---

### Post by Cogito² on 2008-04-27
> **gobbledigook said:**
> any ideas?

If you're just trying to get the windows to boot again you could load up the original windows cd and go into recovery console. From there use "fixmbr" and that should reset the boot sequence to how it was before ubuntu. Though with it that way you probably wouldn't be able to load into ubuntu (and I can't really help you with that).

---

### Post by gobbledigook on 2008-04-28
Hi!

i booted into windows recovery and did FIXMBR, this DID NOT fix my problem it actually exacerbated it! 

after i ran this command my comp booted and i got an error - unmountable/inaccessable partition or something, anyway i gave up... tried a fresh install of Windows to start with, it wouldn't regognise the h/d! said -:partition unwritable, 

so i formatted partition, still windows install failed at reboot! no filesystem found!?!?!?! WTF!?!

then i low level formatted the disk... took ages! and still windows failed at the reboot section of the install!

i removed the drives and installed on an old ide drive, no probs!! BUT when i got into windows and rebooted with all the other drives attached the problem drive was browsable and still had the windows installation files on it!!!

the only thing i can guess is that the drive has something written right at the beginning which is incorrect!!! i have no idea what!

MY ADVICE:- if you wanna install ubuntu on a windows drive.... unplug all other drives FIRST!! and use the auto partition option :)

learn by your mistakes!!

---


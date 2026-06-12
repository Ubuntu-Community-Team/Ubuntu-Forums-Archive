---
title: "Help Needed: NTFS Partition Recovery With testdisk"
date: 2006-01-16
forum: General Help
---

### Post by tmccollum on 2006-01-16
Ok, so here's the deal. I have a dual-boot system set up using three hard drives.  hda holds my Windows system, hdb holds my Linux system and I have a usb harddrive, sda, that I use as a dump for media/documents/etc. However, since sda is formatted in NTFS, I am unable to write to it under Linux. In an effort to make it so that I can read and write to sda, I tried to repartition it using PartitionMagic 8. I wanted to create a new ext3 partition, copy data over to the new partition from the NTFS partition, remove the copied data from the NTFS partition, then expand the ext3 partition until it filled the whole disk. However, in the middle of creating the new partition, PartitionMagic stopped responding. It seems to have deleted the partition table, making it so that I can't even read from the drive. I tried using testdisk under Linux to recover the partition, but this is where I got lost.

Under testdisk, this is the info it lists for sda under the main menu:

Disk /dev/sda - CHS 36481 255 63 - 286165 MB

When I select 'Analyze' for the disk, it gives me this information:

Disk /dev/sda - CHS 36481 255 63 - 286165 MB
Check current partition structure
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 36480 254 63  586067202 [Gargantua]

"Gargantua" is the label of the partition that I want to recover. Under testdisk, I can see that all of the directories and files that were in the partition are still there, but neither Linux nor Windows sees a mountable partition on the disk. Selecting "Save Partition Structure" in testdisk doesn't seem to help. 

Using "fdisk -l", this information is given:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36481   293033601    7  HPFS/NTFS

I'm not sure if that's helpful or not, but I saw that information requested in another thread about a similar topic.

When I try to mount the partition under Linux, I get a Mount Error saying "Unable to mount the selected volume. The volume is probably in a format that cannot be mounted." When I click on "More Details", I get:

"mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount"

The output from dmesg | tail is:
"[4363151.412000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4363151.493000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4363151.493000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4363153.250000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4363153.250000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4363153.922000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4363153.922000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4363197.387000] NTFS-fs warning (device sda1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[4363197.421000] NTFS-fs error (device sda1): load_system_files(): Failed to load $Bitmap.
[4363197.421000] NTFS-fs error (device sda1): ntfs_fill_super(): Failed to load system files."

This is about where my literacy runs out. I'm not sure what steps I need to take to further diagnose the problem or fix it. Can anyone point me in the right direction? Thanks for any help!

---

### Post by LostBear on 2006-01-16
Hi

Ive had issues with partitionmagic in the past. it used to be really stable but i believe its now in the hands of Norton (norton internet security is rubbish so i guess they will mess up part magic to)

i would suggest trying another partition program (partition commander for example or perhaps the company u bought the drive from has some tool i know seagate and maxtor provide such things) or search the web/bittorent for summit called "hirens boot cd" ..it has a load of disk/recovery tools on it and its bootable cd....nice!

lostbear

---

### Post by az on 2006-01-16
I would suggest parted.  Boot from the Ubuntu installer and CTRL-ALt-F2 to the shell.   From there run parted

parted /dev/sda

Use the recovery option to find and reset lost partition to the partition table.

From there, (if you have enough space) image the partition to a file

mkdir /mnt
mount /dev/hdb1 /mnt (assuming that is your ubuntu install)
dd if=/dev/sda1 of=/mnt/home/me/file

Then, boot into ubuntu and use foremost to recover files from your filesystem image.

[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

(You will need to install build-essential to compile foremost.

Good luck.  Your data is probably all recoverable.

If you have no room for an image, you can run foremost on the partition itself.  Just mount it as read-only.

---


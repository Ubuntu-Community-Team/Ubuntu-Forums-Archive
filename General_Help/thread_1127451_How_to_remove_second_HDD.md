---
title: "How to remove second HDD?"
date: 2009-04-16
forum: General Help
---

### Post by kamicosmos on 2009-04-16
I have two 80GB HDD in my system.  The second one is just for storage, the OS (7.10) is on the first one.  I would like to remove the second HDD.  I removed it's mounting line from fstab, and disconnected the drive.  When I boot the system, it takes forever to load, gets to the ubuntu progress bar, takes forever, and then I get dumped to a shell with this error:

Check root=bootarg cat /pro/cmdline
or missing modules, devices : cat/proc/modules ls /dev
ALERT! /dev/disk/by-uuid/(long HDD ID Number here) is missing or not present.

Uh, yeah, I know it's missing or not present, I removed it.  So....what magical trick do I need to do to make the system realize that the second HDD is no longer in the system, and boot normally?

(incidently, I put the second HDD back in, and system boots right up, and even mounts the drive?!  so...I'm pretty confused at this point...)

---

### Post by ajgreeny on 2009-04-16
Can we see the fstab that you edited, with an indication of the line removed or commented out, just in case that is the problem.  It wouldn't normally make that much difference, however, so I think there must be something else going on as well; perhaps a search for a config file of some sort for a program autostarting, or trying to, at boot time.

Let's also see the output of ```
sudo fdisk -l
``` both with and without the second disk installed.

---

### Post by kamicosmos on 2009-04-16
Here's my fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=98529e51-0934-4d25-9063-8bb308b4f5b3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c818f597-4600-4657-ba24-3a744a294211 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdb1	/media/storage 	ext3 	defaults 	0 	1

the HDB1 is the line I removed.

And, here's my fdisk -l output:

> Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf4aff4af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        4863    39019520    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ad523db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc416c416

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9728    78140128+  83  Linux


The 40GB is a Vista install.  (I'm wanting to take the second 80GB, and clone the 40 to it for more room...)

The SDC1 is the second drive I am trying to remove from the 7.10 install.  I think I see one problem, the SDC1 isn't listed in the FSTAB...Hmmmm....

---

### Post by ajgreeny on 2009-04-16
I think perhaps the windows disk is confusing things and that perhaps your disk naming has been upset by the third disk being present.  This is even more confused by your having used /dev/hdb1 in fstab instead of the UUID.  Certainly I am a bit confused, even if your system isn't, so can you show the output of sudo blkid with all disks attached, please.  It may remove some of my confusion at least, even if I still can't sort your problem.

---

### Post by kamicosmos on 2009-04-17
Here is the blkid output:

> /dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0915" TYPE="vfat" 
/dev/sdb1: UUID="98529e51-0934-4d25-9063-8bb308b4f5b3" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdc1: UUID="937d0018-6583-48ef-a89f-866e3c8c5165" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="BE94BF4D94BF06C5" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="c818f597-4600-4657-ba24-3a744a294211" 

---

### Post by ajgreeny on 2009-04-18
OK, thanks for that.  Can you now show the full output of the error including the full UUID when the disk is not connected as that may also throw more light on things, as I'm pretty certain there must be an fstab problem of some kind if it is still trying to mount the removed drive even when you believe you have removed all reference to it from the fstab file.

I am getting even more confused, but I'm sure there must be a simple answer, perhaps even just rewriting from scratch the fstab, but let's keep trying for the moment, and see if we can fix it the easier way first.

---


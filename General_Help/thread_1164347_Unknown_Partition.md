---
title: "Unknown Partition"
date: 2009-05-19
forum: General Help
---

### Post by ShadowNevan on 2009-05-19
Hello everyone! 
I have a problem I installed Ubuntu 9.04 from the live cd it was suppose to dual boot with windows xp. After installation I noticed that GRUb didn't add windows to the boot list. After closer inspection I also discovered that Ubuntu dosent see the original windows partition. I used sudo fdisk -l to check if the partition still exists here is the report:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x058e058d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/sda5            1276        5502    33953346    7  HPFS/NTFS
/dev/sda6            5503        9728    33945313+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ef54e1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        7233    58091040    f  W95 Ext'd (LBA)
/dev/sdb2            7234        9729    20049120   83  Linux
/dev/sdb5               2        7119    57175303+   7  HPFS/NTFS
/dev/sdb6            7120        7233      915673+  82  Linux swap / Solaris

As it turned out the partition still exists and that is correctly recognized as NTFS so I though about using the windows cd to see if the installer would recognize it. To my suprise the windows installer reports the partition as a "Unknown Partition" and that no operating system is installed so I can only format it. Is there a way to restore the partition whitout loosing the data contained on it?

---

### Post by logos34 on 2009-05-19
Are we talking about sda1?

Can you manually mount the drive in ubuntu?

> sudo mkdir /media/sda1

> sudo mount -t ntfs-3g /dev/sda1 /media/sda1

Or use [ntfs-config gui]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.10%20(Intrepid%20Ibex)%20and%20Ubuntu%208.04%20LTS%20(Hardy%20Heron)") to add it to fstab so it automounts.

Anything?


You can add a windows boot entry to menu.lst [like this.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu")

Next, reboot and select windows.  If it doesn't start up, boot the XP install cd, press 'R' to go into Recovery Console, then run this at the C:\ prompt:

> chkdsk /r

---

### Post by ShadowNevan on 2009-05-19
Yes it's sda1 I tried but using the
			 				
sudo mount -t ntfs-3g /dev/sda1 /media/sda1 

but command produces this error

"Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?"

---

### Post by logos34 on 2009-05-19
or try

sudo mount -t **ntfs** /dev/sda1 /media/sda1 (-->this should mount sda1 as read-ony)

maybe it's time to do chkdsk

---

### Post by ShadowNevan on 2009-05-19
Unfortunately the response is the same as in the first case. How can I preform chkdsk in ubuntu?

---

### Post by logos34 on 2009-05-19
> **ShadowNevan said:**
> Unfortunately the response is the same as in the first case. How can I preform chkdsk in ubuntu?

you can't really, you can only flag an ntfs partition as 'dirty', so that it triggers chkdsk when you reboot into xp.

add the windows entry to menu.lst.  

get ntfsprogs:

**sudo apt-get install ntfsprogs**

then,

**sudo ntfsfix /dev/sda1**

> SYNOPSIS
       ntfsfix [options] device

DESCRIPTION
       ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

       You may run ntfsfix on an NTFS volume if you think it  was  damaged  by
       Windows or some other way and it cannot be mounted.


Reboot and select windows in grub menu

---

### Post by ShadowNevan on 2009-05-19
Again no luck this is what I get after using the command

Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

---

### Post by logos34 on 2009-05-19
then do what it says--run chkdsk (either from XP cd or ntfsfix way)

---

### Post by ShadowNevan on 2009-05-19
The problem is that I can't. The partition that is unreadable is also the the main disk containing the windows installation. I have no access to the windows os.

---

### Post by logos34 on 2009-05-19
so, you can't even run the ntfsfix command in ubuntu?  To do it the windows way, you don't need to actually boot windows, just go into the cd recovery console and run chkdsk
(the recovery console is separate from the installer/partitioner/format 

or am I misunderstanding the problem? sorry, trying

---

### Post by ShadowNevan on 2009-05-19
I greatly appreciate your help. But I can't run the recovery console because it's only allowed when the cd installer finds a windows installation. Since the installation partition is unrecognised/damaged/unreadable I can't use this option. And since this whole ordeal began after installin grub I though that there is a tool in ubuntu that can reverse the damage.

---

### Post by logos34 on 2009-05-19
> **ShadowNevan said:**
> I greatly appreciate your help. But I can't run the recovery console because it's only allowed when the cd installer finds a windows installation.

ok, I guess I was wrong...thought it would allow you to enter recovery console.  Been a long time since I had anything to do with XP!

Um, if you cannot install ntfsprogs in ubuntu and run ntfsfix command that way (or maybe you can but grub still can't chainload XP/windows won't respond to chainload), you could try testdisk to fix things (maybe error in the partition table, etc).

sudo apt-get install testdisk

sudo testdisk

Read [this]("http://www.users.bigpond.net.au/hermanzone/p21.html") and [this ]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery")for recovering ntfs partition

good luck

---

### Post by ShadowNevan on 2009-05-19
Thank you!
Your suggestion was right! The problem was a damaged boot sector. I learned much today thanks to you! Again thank you for your support and time.

---

### Post by logos34 on 2009-05-19
> **ShadowNevan said:**
> Thank you!
Your suggestion was right! The problem was a damaged boot sector. I learned much today thanks to you! Again thank you for your support and time.

so, you fixed it [this way]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery"), is that correct?

glad to help steer you to the answer (if only I had suggested testdisk in the very begininng!)

enjoy

---


---
title: "Automount Media Partition at Startup?"
date: 2009-03-22
forum: General Help
---

### Post by antipuls3 on 2009-03-22
I have my music on a separate partition from my Intrepid install, with plans to share the media between both Intrepid and Windows. How would I automount this partition at Intrepid startup so I could listen to music without first mounting it manually? I ran:

cat /etc/fstab

sudo fdisk -l

sudo blkid

and got:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e8eca686-6885-4610-9344-e5791b229051 /               ext3    relatime,errors=remount-ro 0       1
______________________________________________________________
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00011528

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6421    51576651   83  Linux
/dev/sda2            6422       11062    37278832+   7  HPFS/NTFS
/dev/sda3           11063       19457    67432837+   7  HPFS/NTFS
___________________________________________________________________
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00011528

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6421    51576651   83  Linux
/dev/sda2            6422       11062    37278832+   7  HPFS/NTFS
/dev/sda3           11063       19457    67432837+   7  HPFS/NTFS
antipuls3@antipuls3:~$ sudo blkid
/dev/sda1: LABEL="Ubuntu" UUID="e8eca686-6885-4610-9344-e5791b229051" TYPE="ext3" 
/dev/sda2: UUID="7CF53F6C60CC452B" LABEL="Windows" TYPE="ntfs" 
/dev/sda3: UUID="26444E0910C79C2C" LABEL="TransFiles" TYPE="ntfs" 

Where should I go from here? Thanks guys!!!:D

---

### Post by dcstar on 2009-03-23
> **antipuls3 said:**
> I have my music on a separate partition from my Intrepid install, with plans to share the media between both Intrepid and Windows. How would I automount this partition at Intrepid startup so I could listen to music without first mounting it manually? I ran:
.........
Where should I go from here? Thanks guys!!!:D

Install the **pysdm** package and use that.

---

### Post by antipuls3 on 2009-03-23
Ok, so I used that. After playing around with settings for awhile, and after a few restarts, I finally have the harddrive showing up on the desktop when I startup. All my music appears on Rhythmbox, however, I can't play anything. When I attempt to access the drive, I'm informed with the following error:

"Cannot mount volume.
Details>
Unprivileged user can not mount NTFS block devices using the external FUSE. Either mount the volume as root, or rebuild NTFS-3G with intergrated FUSE support and make it setuid root.

What did I do wrong? I can't get on the drive now.. :-(

---

### Post by dcstar on 2009-03-24
> **antipuls3 said:**
> Ok, so I used that. After playing around with settings for awhile, and after a few restarts, I finally have the harddrive showing up on the desktop when I startup. All my music appears on Rhythmbox, however, I can't play anything. When I attempt to access the drive, I'm informed with the following error:

"Cannot mount volume.
Details>
Unprivileged user can not mount NTFS block devices using the external FUSE. Either mount the volume as root, or rebuild NTFS-3G with intergrated FUSE support and make it setuid root.

What did I do wrong? I can't get on the drive now.. :-(

You have to specify the appropriate options to allow user access.

---


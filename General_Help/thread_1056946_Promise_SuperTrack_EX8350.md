---
title: "Promise SuperTrack EX8350"
date: 2009-02-01
forum: General Help
---

### Post by scambro on 2009-02-01
Hi all,

I'm fairly new to Linux, been using it off and on for a year as a LAMP setup on one of my servers, and decided to move to it on my file server because of 2TB raid restrictions on WinXP.  I've got most everything working as I'd like now, except my RAID controller.  

I installed the Linux WebPAM software from Promise, and when I run it, it doesn't see my card.  I have 2 RAID 5 configs built, one that was done on WinXP, and one that I did in the super build utility.  The one from WinXP shows up in my computer, but can't be mounted (says failed to read last sector - maybe you haven't built the RAID yet), and the other does not show at all.  The one from WinXP has about 1.2 TB of data on it, so I don't really want to rebuild it.

I'm obviously missing part of the setup here, but really have no idea what.  I'm running Ubuntu Desktop 8.10.

```
$ sudo cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: Promise  Model: 4 Disk RAID5     Rev: 1.10
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: Promise  Model: 4 Disk RAID5     Rev: 1.10
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi0 Channel: 00 Id: 16 Lun: 00
  Vendor: Promise  Model: RAID Console     Rev: 1.00
  Type:   Processor                        ANSI  SCSI revision: 03
```

Thanks!

---

### Post by scambro on 2009-02-01
I got a little further, but now I'm a bit confused again! :)

I fdisk'ed and formatted the new array (4 x 1.5 TB drives).  After reboot, the drive will show as mounted in my computer, but it shows as 2199 GB.  In a terminal window:

```
$ sudo fdisk -l /dev/sda
Disk /dev/sda: **4500**.7 GB, 4500704329728 bytes
255 heads, 63 sectors/track, 547179 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e0a8c46

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      267349  2147480811   83  Linux

```
```
$ sudo fdisk -l /dev/sda1

Disk /dev/sda1: **2199**.0 GB, 2199020350464 bytes
255 heads, 63 sectors/track, 267348 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda1 doesn't contain a valid partition table

```
When I check the media, I see a mixture of ext 2 and 3 as the filesystem types.  Would that put a limit on the size to 2TB?

I then tried to resize the partition to be 4500, but not really sure what it means by these features, I guess I'll dig around for that for a few...

```
$ sudo parted /dev/sda resize
Partition number? 1                                                       
Start?  [32.3kB]?                                                         
End?  [2199GB]? 4500.7                                                    
Error: File system has an incompatible feature enabled.  Compatible features
are has_journal, dir_index, filetype, sparse_super and large_file.  Use tune2fs
or debugfs to remove features.

```

Thanks!!

---

### Post by scambro on 2009-02-01
I'll keep having a conversation with myself, because I'm learning piece by piece, hopefully it helps someone later when searching around.  I got the new volume setup now, at 4500 GB, and shared with samba.

```
$ sudo parted /dev/sda 
GNU Parted 1.8.9 
Using /dev/sda 
Welcome to GNU Parted! Type 'help' to view a list of commands. 
(parted) mklabel                                                          
Warning: The existing disk label on /dev/sda will be destroyed and all data on 
this disk will be lost. Do you want to continue? 
Yes/No? y                                                                 
New disk label type?  [msdos]? gpt                                        
(parted) mkpart primary 0 4501G 
(parted)                                                                  
(parted) print                                                            
Model: Promise 4 Disk RAID5 (scsi) 
Disk /dev/sda: 4501GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 

Number  Start   End     Size    File system  Name     Flags 
 1      17.4kB  4501GB  4501GB               primary       

(parted) quit                                                             
Information: You may need to update /etc/fstab.                           

```
```
$ sudo mkfs.ext3 /dev/sda1 
mke2fs 1.41.3 (12-Oct-2008) 
Filesystem label= 
OS type: Linux 
Block size=4096 (log=2) 
Fragment size=4096 (log=2) 
274702336 inodes, 1098804759 blocks 
54940237 blocks (5.00%) reserved for the super user 
First data block=0 
Maximum filesystem blocks=0 
33533 block groups 
32768 blocks per group, 32768 fragments per group 
8192 inodes per group 
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848, 512000000, 550731776, 644972544 

Writing inode tables: done                            
Creating journal (32768 blocks): done 
Writing superblocks and filesystem accounting information: 
done 

This filesystem will be automatically checked every 24 mounts or 
180 days, whichever comes first.  Use tune2fs -c or -i to override. 

```
```
$ sudo fsck -f -y /dev/sda1 
fsck 1.41.3 (12-Oct-2008) 
e2fsck 1.41.3 (12-Oct-2008) 
Pass 1: Checking inodes, blocks, and sizes 
Pass 2: Checking directory structure 
Pass 3: Checking directory connectivity 
Pass 4: Checking reference counts 
Pass 5: Checking group summary information 
/dev/sda1: 11/274702336 files (0.0% non-contiguous), 17291319/1098804759 blocks 
$

```

Now I'm off to figure out why my existing RAID5 isn't accessible to Linux.

---


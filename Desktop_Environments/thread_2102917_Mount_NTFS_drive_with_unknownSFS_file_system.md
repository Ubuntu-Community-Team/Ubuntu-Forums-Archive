---
title: "Mount NTFS drive with unknown/SFS file system"
date: 2013-01-08
forum: Desktop Environments
---

### Post by XirWeb on 2013-01-08
Hi :)

I've tried to install Ububntu 12.10 as my FIRST LINUX EXPRIENCE and it failed three times in 'copyng log files' stage of installation progress. anyway, after restart I've found that Ubuntu is installed ad everything is working. that time I've checked drives and all of them mounted properly. because of a problem in VGA I have 're-installed' Ubuntu and this time problem starts...

I have 2 hard disks installed, first one with windows on it and 6 logical drives (which is mounted successfully)  and another hard disk with 2 drives. in windows these 2 drive doesn't have a type (logical/primary) and I think they're dynamic. but both of them have NTFS and are working greatly in windows 7.

I have one of these 2 drives(in second hard disk) mounted automatically and it's working. but problem is about second one, in windows disk manager I can see actually 3 drives in second disk, 2 of them have same name and label, but different sizes. if I jump to my computer then just one drive is shown, which size of that is equal to that two same-name drives.

when I click on that drive in Ubuntu I get this error:
```

Error mounting /dev/sdb3 at /media/developer/Store: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb3" "/media/developer/Store"' exited with non-zero exit status 12: Failed to read last sector (802684927): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb3': Invalid argument
The device '/dev/sdb3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```


and this is output of _fdisk -l_ :
```

Disk /dev/sda: 319.9 GB, 319936615424 bytes
255 heads, 63 sectors/track, 38896 cylinders, total 624876202 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x488a4889

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    76838894    38419416    7  HPFS/NTFS/exFAT
/dev/sda2        76838956   602007551   262584298    f  W95 Ext'd (LBA)
/dev/sda5        76838958   138271454    30716248+   7  HPFS/NTFS/exFAT
/dev/sda6       138271518   199704014    30716248+   b  W95 FAT32
/dev/sda7       199704078   322565605    61430764    7  HPFS/NTFS/exFAT
/dev/sda8       384001758   445434254    30716248+   7  HPFS/NTFS/exFAT
/dev/sda9       445434318   486400004    20482843+   7  HPFS/NTFS/exFAT
/dev/sda10      486400068   527365754    20482843+   7  HPFS/NTFS/exFAT
/dev/sda11      527365818   588846509    30740346    7  HPFS/NTFS/exFAT
/dev/sda12      601335808   602007551      335872   82  Linux swap / Solaris
/dev/sda13      322566144   383999999    30716928   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe2752b79

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976771119   488385528+  42  SFS

```


here is _parted -l _:
```

Model: ATA MAXTOR STM332082 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  39.3GB  39.3GB  primary   ntfs            boot
 2      39.3GB  308GB   269GB   extended                  lba
 5      39.3GB  70.8GB  31.5GB  logical   ntfs
 6      70.8GB  102GB   31.5GB  logical   fat32
 7      102GB   165GB   62.9GB  logical   ntfs
13      165GB   197GB   31.5GB  logical   ext4
 8      197GB   228GB   31.5GB  logical   ntfs
 9      228GB   249GB   21.0GB  logical   ntfs
10      249GB   270GB   21.0GB  logical   ntfs
11      270GB   301GB   31.5GB  logical   ntfs
12      308GB   308GB   344MB   logical   linux-swap(v1)


Model: ATA ST3500418AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label         
```


also, I've tried this:
```

sudo mount -t ntfs /dev/sdb2 /media/sdb2 -o defaults,umask=0

```

result:
```

NTFS signature is missing.
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```


I'm really tired of searching and reading...
Really great job, Ubuntu, but Linux is yet scary cuz of such problems for me.
although there is a good sense after solving problems in geeky way, such what I've did with problem of setting FullHD res for my monitor :D


please help me!
thank you people

---

### Post by oldfred on 2013-01-08
SFS is dynamic partitioning by Windows. Normally it does that instead of the usual extended & logical partitions when you want to create more than the 4 allowed primary partitions.

       Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

   Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
 GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

    can I mount my WinXP software RAID 0 array in Ubuntu/Kubuntu? dynamic use mdadm
[http://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk](http://ubuntuforums.org/showthread.php?t=833653&highlight=dynamic+disk)

    If not rebooted recover partition:
[http://ubuntuforums.org/showpost.php?p=10364557&postcount=34](http://ubuntuforums.org/showpost.php?p=10364557&postcount=34)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Not sure if in "free" version, but older version had it & was free see 4.2:
[http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html)
[http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm](http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm)
[http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/](http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/)

---

### Post by XirWeb on 2013-01-08
Oh-uh!
thank you so much,
I didn't know about SFS before this...
let me try one of this options (Minitool partition wizard Home).

thanks again :)

---

### Post by oldfred on 2013-01-08
The home or free versions all used to include conversion. But they are converting to only including that in the upgrade or paid versions. Not sure if both have converted or if any others have the same capability. Other software download sites may have the older versions still available.

---

### Post by XirWeb on 2013-01-09
yes you are right... I've spent whole night searching with red eyes staring at monitor!
finally founded 2 of those programs and NO CHANCE, they can just convert simple or mirrored disks, it seems my case is not defined for them. I've also tried a cool tool named "testDisk" but it's whole command line based and without any backup its really scary to do anything.

what can I do now?! I heard somewhere that its provided in new linux cores to support windows dynamic drives but mainstreams like Ubuntu just ignored that in compile. I'm going to delete Ubuntu and try to free up some space, then repeat: "shrink one of drives in disk, expand other one" untill remains just one drive in dynamic disk, so I can use those softwares you have recommended. 

Stupid, 
but I don't know even why it's "dynamic"
and when I converted it?  I simply hate it :D ah.

---

### Post by oldfred on 2013-01-09
There now is just some support for SFS starting in Linux and it causes the bug in grub2 2.00 with 12.10. But I do not think Linux works with SFS, just that grub was trying to allow chain loading into it. LDM seems to be another name for SFS or dynamic?

GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+s...2/+bug/1061255]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255")

---

### Post by XirWeb on 2013-01-09
When I've 2 partitions in my dynamic disk, it actually recognized and mounted the first one! I think it's yet just BUGGY to be included. with a real pain, I've merged 2 partitions in 1 simple partition in my dynamic disk but... again that programs have no thing to do. they just support disks with 1 contiguous single partition, mine is 5 parts!

Changing partition type id to _ntfs(7)_ doesn't works... windows just lost partition, Ubuntu now finds it as "ntfs" but with corrupted ntfs table. and... I don't know what to do! I hope people here can find the solution for me... I've changed it back to sfs(42).

finally I've re-installed Ubuntu, but before that I've tried to install Mint 14 but that bug you've mentioned makes it hang during installation. I'm in love with Ubuntu and Linux, but this problem...!

an image attached that shows current setup of partition in *Disks*.
thank you .

---

### Post by oldfred on 2013-01-09
You really have to remove the dynamic partitions, but it is not straight forward or else Microsoft would not say backup & totally repartition and reinstall.

Dynamic means it is  a logical partition that does not have to be the same as the physical partitions. Linux will see the physical partitions.  But Windows using the dynamic may have part of a partition in one physical partition and part in another.

---

### Post by XirWeb on 2013-01-10
ayy... wasted time for nothing!
thank you olfred, really good support.

yeas it's a BIG problem and I'm going back to windows for now. I've installed VirtualBox thanks to free size remained after deleting Ubuntu, it was slow but after installing guest features now is working almost good. 

this problem-solving challenges showed me other side of "linux man" and I should admit windows is yet far better for ME, personally. with Virtual machine I can learn Linux and come back when matured. 

thank you again,
bye :)

---

### Post by oldfred on 2013-01-10
Whatever works. :)

It only took me a while to mostly convert to Linux, but I had one app in Windows that had me dual booting for about 5 years. Only last year did I finally shut down XP as it did not easily add new drivers for AHCI and I had to have AHCI for my SSD.

I prefer having different operating systems on different drives, but laptops usually have only one drive. Ubuntu will work from a USB drive, but of course is not as fast as a SATA port drive. With newer systems now having USB3 ports (and some of the newest actually working for boot drives) and external drive may be a reasonable choice.

A lot of users like virtual installs for the ease of changing back & forth, but you lose some performance, so gaming and some application do not run as fast.

---

### Post by rodrigokay on 2013-09-09
[COLOR=#000000]maybe this helps.... [/COLOR]http://packages.ubuntu.com/km/saucy/otherosfs/ldmtool

---


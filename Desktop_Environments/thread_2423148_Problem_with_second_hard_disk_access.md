---
title: "Problem with second hard disk access"
date: 2019-07-18
forum: Desktop Environments
---

### Post by tarek-badr on 2019-07-18
Hey everyone, 

i am a bit new to Ubuntu and have a small problem accessing my second Hard disk, i have a main ssd one where ubuntu is installed, and a second extra one but i do't know how to access it or move files to it!

here is what i get when i give the command sudo parted -l


Error: /dev/sda: unrecognised disk label
Model: ATA ST2000LM007-1R81 (scsi)                                        
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 


Model: Unknown (unknown)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  840MB   839MB   fat32        EFI system partition  boot, esp
 2      840MB   6209MB  5369MB  fat32        Basic data partition  msftres
 3      6209MB  512GB   506GB   ext4

Thanks in advance!

---

### Post by Autodave on 2019-07-18
I am sure that someone with a lot more experience than myself will respond, but to me it looks like the drive isn't formatted?  Was this a new drive?  Has anything ever been on it?  If not new, was the drive previously used on a Windows machine?

---

### Post by TheFu on 2019-07-18
Looks like  /dev/sda needs a partition table, partitioning and formatting.  I would use **gparted** for that, choose GPT, not MBR/MSDOS.
This assumes  /dev/sda is the drive you mean.  If you want any data that is on it, this will wipe everything, 100%.

After you format one of the partitions with a file system, use EXT4 unless you have good reason for some other file system, then you can mount it almost anywhere. Use the fstab for that. Google will find a guide - "ubuntu fstab" is the search term.

BTW, if 
```
 3 6209MB 512GB 506GB ext4
```
is being used for / on the NVMe, I'd reduce that as much as possible - 25G for the OS is vastly more than needed.  Then I'd setup /home on the NVMe with another partition - probably around 20G for everything except media. Then I'd put media on the spinning disk and use symbolic links to make access easier.  I wouldn't directly mount the spinning disk anywhere under HOME.

BTW, it is considered a best practice to leave 10-20% of an SSD unused. This should drastically extend the SSD life.

If you are really adventurous and want a much more flexible storage management solution, use LVM. Then resizing storage areas up is trivial and down it is much easier.

---

### Post by oldfred on 2019-07-18
Would you ever want to install a second copy of Ubuntu to test or experiment with settings so you do not potentially mess up main working install. Or try a different flavor? If so include an ESP - efi system partition FAT32 as first partition, 100 to 500MB. 

      Detailed instructions on moving /home.
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[https://ubuntuforums.org/showthread.php?t=2343317](https://ubuntuforums.org/showthread.php?t=2343317)

Another alternative is to use data partition(s). You can mount in / and link folders back into /home or directly link into /home. But with your own data partition best to understand mounting, ownership & permissions. Using /home automatically does all that. But if a bit more knowledgeable or willing to experiment/learn you can use data partition.

Be sure to choose gpt before anything else in partitioning. See attached.
       Also links to more info, gparted is included in Ubuntu live installer, but you can add it to your install to work on other drives, just not on any mounted partitions.
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
[https://gparted.org/news.php](https://gparted.org/news.php)

---

### Post by tarek-badr on 2019-09-11
Thanks a lot for your reply. Yes its a new drive and have never been used, i thought it would have been delivered formatted and accessible but apparently this is not the case. I have already much important data on the mounted SSD, so what would be the best way to format and access the extra hard disk, without risking the SSD data where also the OS runs?

---

### Post by tarek-badr on 2019-09-11
> **TheFu said:**
> Looks like  /dev/sda needs a partition table, partitioning and formatting.  I would use **gparted** for that, choose GPT, not MBR/MSDOS.
This assumes  /dev/sda is the drive you mean.  If you want any data that is on it, this will wipe everything, 100%.

After you format one of the partitions with a file system, use EXT4 unless you have good reason for some other file system, then you can mount it almost anywhere. Use the fstab for that. Google will find a guide - "ubuntu fstab" is the search term.

BTW, if 
```
 3 6209MB 512GB 506GB ext4
```
is being used for / on the NVMe, I'd reduce that as much as possible - 25G for the OS is vastly more than needed.  Then I'd setup /home on the NVMe with another partition - probably around 20G for everything except media. Then I'd put media on the spinning disk and use symbolic links to make access easier.  I wouldn't directly mount the spinning disk anywhere under HOME.

BTW, it is considered a best practice to leave 10-20% of an SSD unused. This should drastically extend the SSD life.

If you are really adventurous and want a much more flexible storage management solution, use LVM. Then resizing storage areas up is trivial and down it is much easier.


Thanks a lot for your reply. It is a new drive and have never been used. I have already much important data on the mounted SSD, so what would be the best way to format and access the extra hard disk, without risking the SSD data where also the OS runs? Would using gparted affect the other drive where the OS runs. Sorry if my questions are quite basic but still new to Linux here

---

### Post by Dennis N on 2019-09-11
> Would using gparted affect the other drive where the OS runs. Sorry if my questions are quite basic but still new to Linux here
No, there is a drive selector in the upper right of the gparted window. That displays the drive gparted will change.

---

### Post by oldfred on 2019-09-11
MBR(for old BIOS) or gpt(for UEFI) partitions:
[URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace

      [/URL]
 gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions) 
    

See attached screen shots for gparted, first select gpt (double check you are using sdb), example of many partitions on sdb.
[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by TheFu on 2019-09-11
> **tarek-badr said:**
> Thanks a lot for your reply. Yes its a new drive and have never been used, i thought it would have been delivered formatted and accessible but apparently this is not the case. I have already much important data on the mounted SSD, so what would be the best way to format and access the extra hard disk, without risking the SSD data where also the OS runs?

If you are running Linux, never assume anything.  You don't want to use NTFS if you can avoid it. There are many reasons why that is a bad choice.

NTFS is **not** a standard.  Many things that people used to MS-Windows think ARE NOT standards.  Linux cannot be run on NTFS, for example.

---


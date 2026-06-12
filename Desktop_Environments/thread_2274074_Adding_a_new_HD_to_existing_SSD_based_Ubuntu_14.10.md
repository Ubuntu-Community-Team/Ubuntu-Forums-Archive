---
title: "Adding a new HD to existing SSD based Ubuntu 14.10 Desktop"
date: 2015-04-17
forum: Desktop Environments
---

### Post by eightbits2010 on 2015-04-17
I recently purchased desktop in which Ubuntu 14.10 came installed.  
 It came with a 120 GB SSD SATA drive installed and currently is the only drive installed.
 
 
  I am planning on adding a SATA HD of 1TB and I am not sure  what part of the existing SSD file
 structure to copy/move to a new  HD.  
 
 
 I am thinking I can move everything from the existing SSD Home directory to the new HD ?
I am attempting to decrease the amount of writes and disk activity utilizing the SSD.  

 
 
 I am looking for some suggestions on the proper configuration of a added HD and what is the best approach 
of the files from the SSD to move to a new HD(?).

---

### Post by oldfred on 2015-04-17
Lots of alternatives.

My choice is to have all of / (root) including /home, but none of the data folders nor some hidden folders like the Firefox & Thunderbird profiles that have lots of data on SSD. Then I have all my data on my hard drive in a /mnt/data partition so not seen in Nautilus (unless I drill down to it) and link all the folders into /home.
Then all the system is on the faster drive and all the data which is not used as much is on slower drive.
I also have other partitions, I do a backup to/from each drive of some of the most critical data, but do not really consider it a real backup as it is not archiving data. My copies to DVDs then have the archives. I also have partitions for other installs & ISOs which is use with grub to directly boot.

```
fred@trusy-ar:~$ sudo parted -l
[sudo] password for fred: 
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name     Flags
 1      1049kB  525MB   524MB   fat32           efi      boot
 2      525MB   527MB   2097kB                           bios_grub
 3      527MB   26.7GB  26.2GB  ext4            trusty
 6      121GB   121GB   105MB   fat32                    msftdata
 5      121GB   126GB   5163MB  ext4            iso_ssd
 4      126GB   128GB   2000MB  linux-swap(v1)


Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  525MB   524MB   fat32           EFI System Partition  boot
 2      525MB   527MB   2097kB                                        bios_grub
 3      527MB   26.7GB  26.2GB  ext4            vivid
 4      26.7GB  446GB   419GB   ext4            data
 5      446GB   476GB   29.9GB  ext4            backup
 8      711GB   713GB   2000MB  linux-swap(v1)
 7      713GB   993GB   280GB   ext4            homerun
 6      993GB   1000GB  7337MB  ext4            iso_hdd


```

I started splitting /home as I multi-boot, but with SSD same idea is one possibility.

 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by eightbits2010 on 2015-04-17
Thanks oldfred: That may be a little more complicated than I hoped. I did not think of the Firefox and Thunderbird folders. I think they are hidden. My biggest concern was the constant writing to the SSD and the limitations concerning that. I did notice on a backup to an external (USB) HD that the .mozilla had a very large number of files which I did not figure out
what they are for and can they be deleted.
I was thinking that all I might have to do is install , partition and format and then just  copy/move the complete /Home to the newly installed HD. 
You have supplied a lot of things for me to figure out what to do and a better configuration. I was under the impression that it was much better to have only the bare OS files to properly run Ubuntu (using 14.10) and most everything else reside on the second HD.

---

### Post by oldfred on 2015-04-17
A simple choice is just to have / on SSD and /home on hard drive. 
And if a newer user that is fine. I might save room on SSD for another install just so you can test other versions and perhaps data partition(s) on hard drive to learn about mounts, ownership & permissions.

But a few of the files in /home are your user settings which are accessed a lot more and the hidden files & folders, most are data, but some are used a bit more like the profiles. I do regularly houseclean profiles and run a script to vacuum the sqlite files.

I also recommend using gpt whether you use BIOS or UEFI. Then drive is more compatible with the newer UEFI systems in case you later do move drive to a new system. I like to add efi partition even if not used as it can be difficult to add later. 

And I like to have an install on the hard drive that can boot without the SSD. 
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive.

---

### Post by eightbits2010 on 2015-05-09
[SIZE=2]Well, I have the 1TB HD installed and it seems to work. However, I do have some concerns that[/SIZE]
 [SIZE=2]it is possible I did not get the mount location correct and have to wonder about the long id[/SIZE]
 [SIZE=2]/mnt/9ba04247-82cf-4aeb-93c8-ac6794d3a16a$ that seems to be assigned to the drive.[/SIZE]
 
 
 [SIZE=2]I am attaching a odt file that contains text from terminal listings as well as graphical tools.[/SIZE]
 
 
 [SIZE=2]If there is a more correct way to add the drive or  a better way , I would appreciate comments or[/SIZE]
 [SIZE=2]suggestions.[/SIZE]
oldfred, thanks for your suggestions.

fiIrst download was incorrect.    [ATTACH=CONFIG]261856[/ATTACH] post_to_ubun.odt is correct.

---

### Post by oldfred on 2015-05-09
Not sure how you mounted it?
Was that manually using UUID, Disks or with fstab?

I label all partitions so any automounts of ones I only use sometimes use label.
I create mount points with descriptions for those I mount in fstab.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)
And you get into permissions & ownership:

 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

This is how I manually mount & change ownership and permissions:

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

And this is what I follow to create new fstab entry. I copy & paste with my mount & UUID.
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by eightbits2010 on 2015-05-09
Thanks oldfred. I will examine your helpful links. Question: I am sure I can start over on the 1TB drive. I am thinking I can either er format the drive or partition ??? I do see you commented that you prefer to mount at /mnt. WHat about that very long name for the assigned to the drive: [SIZE=2]/mnt/9ba04247-82cf-4aeb-93c8-ac6794d3a16a$  ? I don't think I have ever seen any assignment like that before![/SIZE]

---

### Post by oldfred on 2015-05-09
That is just the UUID. 
And when letting system auto mount in /media that is often used.

But that is why I asked how you created the /mnt/UUID entry? As I have not seen that, or not often at least. Most have created a mount and then used that. I have used /mnt/data, /mount/shared for a NTFS formatted partition, /mnt/backup, /mnt/ISO etc without issues other than ownership & permissions which you must set.

---


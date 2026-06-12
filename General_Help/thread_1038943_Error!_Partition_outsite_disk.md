---
title: "Error! Partition outsite disk"
date: 2009-01-14
forum: General Help
---

### Post by thegreat on 2009-01-14
Hi,
I have a problem when I try booting GParted from a live cd or running it in Ubuntu I get this error:
```

======================
libparted : 1.8.9
======================
Can't have a partition outside the disk!

```

GParted then opens but declares my hd as 300gb of unallocated space. I believe this is because I have corrupted the partition table.

fdisk from within ubuntu
```

sudo fdisk -l

```
returns this:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009b837

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008   83  Linux
/dev/sda2            2433       10718    66557292   83  Linux
/dev/sda3   *       10719       13315    20860396+   7  HPFS/NTFS
/dev/sda4           13316       38914   205623967+   f  W95 Ext'd (LBA)
/dev/sda5           13316       15865    20480000    7  HPFS/NTFS
/dev/sda6           15866       28613   102398278+   7  HPFS/NTFS
/dev/sda7           28614       38403    78638143+   7  HPFS/NTFS

```
Briefly:
sda1 is an Ubuntu installation
sda2 is my /home
sda3 is a windows xp installation
sda5 is a Windows 7 beta installation (I was curious - I think it was the built-in partition editor that caused this problem =S)
sda6 and sda7 contain media and work documents
*sda8 was a 4gb logical swap  partition but I deleted it as it was ending outside the 38913 cylinders. (I thought I might be able to resize sda4 after removing it then recreate the swap partition).

All the OS installations boot (with GRUB) and run fine. The only thing that is concerning is that GParted wont read my hard disk. After a few hours of Googling i am pretty sure the problem is to do with my disk having 38913 cylinders and the extended partition (sda4) ending on 38914. Is there a way I can correct the boundaries of sda4 without losing any data from the logical partitions within it? Or is this even a serious issue? It would be nice to get a swap partition again in any case =P

I found this post in ubuntu forums: (excuse the google cache, the forums have been down all day).

[http://ubuntuforums.org/archive/index.php/t-352723.html]("http://ubuntuforums.org/archive/index.php/t-352723.html")

The above post seems to be about a similar problem. User houseam suggests deleting the extended partition with fdisk then creating a new one within the cylinder boundaries. I am unsure whether it is safe to do this however as I am not too keen on unnecessarily losing the logical partitions.

If anyone can offer me some advice it would be greatly appreciated.
Thanks,
Tom

---

### Post by pavel989 on 2009-01-14
First advice, ALWAYS WORK IN POWERS OF 4. hard drives like 4. 
Now, personally i think the way to go, would be to back everything up, and delte a few and move em around. 

id look into the id's of the 4 part's being 7, and the other f. looks, weird...

---

### Post by caljohnsmith on 2009-01-14
> **thegreat said:**
> 

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, [COLOR="Red"]38913[/COLOR] cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009b837

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008   83  Linux
/dev/sda2            2433       10718    66557292   83  Linux
/dev/sda3   *       10719       13315    20860396+   7  HPFS/NTFS
/dev/sda4           13316       [COLOR="Red"]38914[/COLOR]   205623967+   f  W95 Ext'd (LBA)
/dev/sda5           13316       15865    20480000    7  HPFS/NTFS
/dev/sda6           15866       28613   102398278+   7  HPFS/NTFS
/dev/sda7           28614       38403    78638143+   7  HPFS/NTFS

```

It looks like you're right, the extended partition ending point exceeds the maximum number of cylinders of your drive (38914 > 38913), and that's why gparted is complaining. If that's the only problem with your partition table, it should be easy to correct, so how about posting:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want.

---

### Post by thegreat on 2009-01-14
Thanks for the quick response guys.

Here are the results:
sudo fdisk -lu
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009b837

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    39070078    19535008   83  Linux
/dev/sda2        39070080   172184663    66557292   83  Linux
/dev/sda3   *   172184670   213905462    20860396+   7  HPFS/NTFS
/dev/sda4       213905475   625153409   205623967+   f  W95 Ext'd (LBA)
/dev/sda5       213907456   254867455    20480000    7  HPFS/NTFS
/dev/sda6       254871288   459667844   102398278+   7  HPFS/NTFS
/dev/sda7       459667908   616944194    78638143+   7  HPFS/NTFS

```

sudo sfdisk -d
```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 39070016, Id=83
/dev/sda2 : start= 39070080, size=133114584, Id=83
/dev/sda3 : start=172184670, size= 41720793, Id= 7, bootable
/dev/sda4 : start=213905475, size=411247935, Id= f
/dev/sda5 : start=213907456, size= 40960000, Id= 7
/dev/sda6 : start=254871288, size=204796557, Id= 7
/dev/sda7 : start=459667908, size=157276287, Id= 7

```

Cheers

---

### Post by caljohnsmith on 2009-01-14
OK, so it looks like the only problem with your partition table is that the sda4 extended partition ends at a point past the end of the drive, because it ends on sector 625153409 while the HDD only has 625142448 sectors. Fortunately correcting that type of problem is usually easy, so how about doing the following:
```
echo "213905475,411236974,f" | sudo sfdisk -f -uS /dev/sda -N4 -O sda_sectors_modified.save
```
Please post the output of the above command. Also, the above command will create a small "sda_sectors_modified.save" file to your desktop; please save that file to another drive or some place like your email account, just not on the same drive as sda. If for any reason something were to go wrong with the sfdisk command above, all you need is the "sda_sectors_modified.save" file in order to restore your HDD/partition table back to its original state, so that is your insurance against any possible problems. Next reboot, and once you get back into Ubuntu, please post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print
```
And we can work from there. :)

---

### Post by thegreat on 2009-01-14
Ok, that spits this out:
```

tom@labuntu:~$ echo "213905475,411236974,f" | sudo sfdisk -f -uS /dev/sda -N4 -O sda_sectors_modified.save
[sudo] password for tom: 
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63  39070078   39070016  83  Linux
/dev/sda2      39070080 172184663  133114584  83  Linux
/dev/sda3   * 172184670 213905462   41720793   7  HPFS/NTFS
/dev/sda4     213905475 625142448  411236974   f  W95 Ext'd (LBA)
/dev/sda5     213907456 254867455   40960000   7  HPFS/NTFS
/dev/sda6     254871288 459667844  204796557   7  HPFS/NTFS
/dev/sda7     459667908 616944194  157276287   7  HPFS/NTFS
Warning: given size (411236974) exceeds max allowable size (411231870)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63  39070078   39070016  83  Linux
/dev/sda2      39070080 172184663  133114584  83  Linux
/dev/sda3   * 172184670 213905462   41720793   7  HPFS/NTFS
/dev/sda4     213905475 625142448  411236974   f  W95 Ext'd (LBA)
/dev/sda5     213907456 254867455   40960000   7  HPFS/NTFS
/dev/sda6     254871288 459667844  204796557   7  HPFS/NTFS
/dev/sda7     459667908 616944194  157276287   7  HPFS/NTFS
Warning: partition 4 extends past end of disk
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

Should I boot a live disk (ubuntu/knoppix) and try this again?
Thanks heaps for your help!

---

### Post by caljohnsmith on 2009-01-14
> **thegreat said:**
> 
Should I boot a live disk (ubuntu/knoppix) and try this again?
Thanks heaps for your help!
Your sda4 extended partition now ends on the last sector of the drive as planned, so I think you should be fine. How about rebooting and posting the output of the commands at the end of post #5, and we can work from there.

---

### Post by thegreat on 2009-01-14
Sorry I jumped to conculsions about the errors, here is the output:
sudo fdisk -lu
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009b837

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    39070078    19535008   83  Linux
/dev/sda2        39070080   172184663    66557292   83  Linux
/dev/sda3   *   172184670   213905462    20860396+   7  HPFS/NTFS
/dev/sda4       213905475   625142448   205618487    f  W95 Ext'd (LBA)
/dev/sda5       213907456   254867455    20480000    7  HPFS/NTFS
/dev/sda6       254871288   459667844   102398278+   7  HPFS/NTFS
/dev/sda7       459667908   616944194    78638143+   7  HPFS/NTFS

```

sudo sfdisk -d
```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 39070016, Id=83
/dev/sda2 : start= 39070080, size=133114584, Id=83
/dev/sda3 : start=172184670, size= 41720793, Id= 7, bootable
/dev/sda4 : start=213905475, size=411236974, Id= f
/dev/sda5 : start=213907456, size= 40960000, Id= 7
/dev/sda6 : start=254871288, size=204796557, Id= 7
/dev/sda7 : start=459667908, size=157276287, Id= 7

```

sudo parted /dev/sda print
```

Error: Can't have a partition outside the disk!   

```

Cheers,
Tom

---

### Post by caljohnsmith on 2009-01-14
I didn't think that having the extended partition end on the last sector of the drive would cause any problems, but it looks like parted is still complaining about it. But that's OK, how about we just make sda4 end on a cylinder boundary before the end of the drive, and hopefully parted will be happy with that. How about doing:
```
echo "213905475,411231871,f" | sudo sfdisk -f -uS /dev/sda -N4 -O sda_sectors_modified.save
```
And again reboot, post the output of the commands at the end of post #5 again, and we can work from there.

---

### Post by thegreat on 2009-01-14
This looks better :)

sudo fdisk -lu
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009b837

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    39070078    19535008   83  Linux
/dev/sda2        39070080   172184663    66557292   83  Linux
/dev/sda3   *   172184670   213905462    20860396+   7  HPFS/NTFS
/dev/sda4       213905475   625137345   205615935+   f  W95 Ext'd (LBA)
/dev/sda5       213907456   254867455    20480000    7  HPFS/NTFS
/dev/sda6       254871288   459667844   102398278+   7  HPFS/NTFS
/dev/sda7       459667908   616944194    78638143+   7  HPFS/NTFS

```

sudo sfdisk -d
```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 39070016, Id=83
/dev/sda2 : start= 39070080, size=133114584, Id=83
/dev/sda3 : start=172184670, size= 41720793, Id= 7, bootable
/dev/sda4 : start=213905475, size=411231871, Id= f
/dev/sda5 : start=213907456, size= 40960000, Id= 7
/dev/sda6 : start=254871288, size=204796557, Id= 7
/dev/sda7 : start=459667908, size=157276287, Id= 7

```

sudo parted /dev/sda print
```

Model: ATA ST9320320AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  20.0GB  20.0GB  primary   ext3              
 2      20.0GB  88.2GB  68.2GB  primary   ext3              
 3      88.2GB  110GB   21.4GB  primary   ntfs         boot 
 4      110GB   320GB   211GB   extended               lba  
 5      110GB   130GB   21.0GB  logical   ntfs              
 6      130GB   235GB   105GB   logical   ntfs              
 7      235GB   316GB   80.5GB  logical   ntfs  

```

:) Thanks!

---

### Post by caljohnsmith on 2009-01-14
Great, looks like you're finally in business. Cheers and good luck with whatever repartitioning you intend to do with gparted. :)

---

### Post by thegreat on 2009-01-14
Once again thank you very very much for the help and extremely quick responses! 

Now I will restore my swap partition and forget about messing with my partition table (and data) for awhile :D

Thanks again,
Tom

---

### Post by caljohnsmith on 2009-01-14
> **thegreat said:**
> Once again thank you very very much for the help and extremely quick responses! 

Now I will restore my swap partition and forget about messing with my partition table (and data) for awhile :D

Thanks again,
Tom
You're certainly welcome, but I just wanted to warn you of one of the "gotchas" that can often happen when recreating your swap file; it would be good to reassign the old swap partition UUID to the new swap partition, because otherwise you will have to modify your /etc/fstab, /etc/initramfs-tools/conf.d/resume file, and also regenerate all your initrd images so they will have the new swap partition UUID. So after you create your new swap file, if you would like a hand changing the swap partition UUID to the UUID of your original swap partition, how about posting:
```
sudo mount /dev/sda1 /mnt
cat /mnt/etc/fstab
cat /mnt/etc/initramfs-tools/conf.d/resume
sudo blkid -c /dev/null
```
And we can go from there if you want.

---

### Post by MarcusXP on 2010-02-09
I have a very similar problem, can you help me as well please?
My extended partition ends also beyond the max size of the drive.. also there seem to be some other issues as well, like: "start: (c,h,s) expected (1023,254,63) found (1023,0,1)"

```
Skeleton ~ # fdisk -l /dev/sda

Disk /dev/sda: 343.6 GB, 343595286528 bytes
255 heads, 63 sectors/track, 41773 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Disk identifier: 0x40e56b55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          33      265041   83  Linux
/dev/sda2              34        6814    54468382+  83  Linux
/dev/sda3            6815        8903    16779892+  83  Linux
/dev/sda4            8904       46864   304921732+   5  Extended
/dev/sda5            8904       10470    12586896   82  Linux swap / Solaris
/dev/sda6           10471       36237   206973396    7  HPFS/NTFS
``````

Skeleton ~ # sfdisk -l /dev/sda

Disk /dev/sda: 41773 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+     32      33-    265041   83  Linux
/dev/sda2         33    6813    6781   54468382+  83  Linux
/dev/sda3       6814    8902    2089   16779892+  83  Linux
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4       8903   46863   37961  304921732+   5  Extended
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda5       8903+  10469    1567-  12586896   82  Linux swap / Solaris
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda6      10470+  36236   25767- 206973396    7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)
``````
Skeleton ~ # sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   530082, Id=83, bootable
/dev/sda2 : start=   530145, size=108936765, Id=83
/dev/sda3 : start=109466910, size= 33559785, Id=83
/dev/sda4 : start=143026695, size=609843465, Id= 5
/dev/sda5 : start=143026758, size= 25173792, Id=82
/dev/sda6 : start=168200613, size=413946792, Id= 7
```
I am using Gentoo, and I switched as root in the console so I don't need to use any "sudo" commands.

Thanks a lot!

---

### Post by einstein1969 on 2010-02-11
@marcusXP

I have a similar problem.

My problem is created when i used fdisk advanced option "[B]fix partition order".

[/B]is your case?

---

### Post by Gani Utomo on 2010-02-12
I had the same problem.
After I "**fix partition order**" using **fdisk**, I got **grub console>**
And when using **GParted** from ubuntu 9.10 Live CD, my entire hard drive is "**unalocated **".
But I still can read all data by mounting every partition.

Any suggestion?

---

### Post by einstein1969 on 2010-02-13
in the gnu fdisk there is a warning for the user

```
   
/* We will issue warning to the user for now */
   if (PED_EXCEPTION_CANCEL == ped_exception_throw(PED_EXCEPTION_WARNING,
                     PED_EXCEPTION_IGNORE_CANCEL,
                     "Fixing partition order "
                     "is experimental. Use "
                     "at your own risk."))
      return 0;

```but in the original??? fdisk there isn't...

the solux proprosed in a comment in fdisk (util-linux) is:

```

* Fix the chain of logicals.
 * extended_offset is unchanged, the set of sectors used is unchanged
 * The chain is sorted so that sectors increase, and so that
 * starting sectors increase.

* After this it may still be that cfdisk doesnt like the table.
* (This is because cfdisk considers expanded parts, from link to
* end of partition, and these may still overlap.)
* Now
*   **sfdisk /dev/hda > ohda; sfdisk /dev/hda < ohda**
* may help.

```but this solution in my case destroy a partition...

i suggest to backup sector in this way:

assume /dev/hda is your disk device

```

**sfdisk /dev/hda > ohda**

```and then

```

**sfdisk ****-uS ****/dev/hda -O sector.save  < ohda**

```then backup sector.save in secure place and check anything partition. 

and, if there is problem, restore in this way:

```

**sfdisk /dev/hda -I sector.save**

```RIF: [http://forum.ubuntu-it.org/index.php/topic,308613.msg2807030.html#msg2807030](http://forum.ubuntu-it.org/index.php/topic,308613.msg2807030.html#msg2807030)

---

### Post by tollboy on 2010-03-31
Thanx john you made my day

---

### Post by Pip_ on 2011-01-31
Hey

can somebody help me do something with this?

fdisk -lu
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      [COLOR=Red]  2048[/COLOR]    54315000    27156476+   7  HPFS/NTFS   <- Windows
/dev/sda2        54317056   106864639    26273792   83  Linux <- Ubuntu /
/dev/sda3       106866688   189288447    41210880   83  Linux <- Ubuntu /home
/dev/sda4       189288477   [COLOR=Red]390732929[/COLOR]   100722226+   f  W95 Ext'd (LBA)
/dev/sda5       189290496   197631983     4170744   82  Linux swap / Solaris
/dev/sda6       197634048   390719487    96542720    7  HPFS/NTFS <- data from old system

```sfdisk -d
```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 54312953, Id= 7, bootable
/dev/sda2 : start= 54317056, size= 52547584, Id=83
/dev/sda3 : start=106866688, size= 82421760, Id=83
/dev/sda4 : start=189288477, size=201444453, Id= f
/dev/sda5 : start=189290496, size=  8341488, Id=82
/dev/sda6 : start=197634048, size=193085440, Id= 7

```i'm trying to do this since few days and i don't know how :/

---

### Post by oldfred on 2011-01-31
It looks like your extended is bigger or extends beyond the end of the drive.

Back up a copy of your partition table on save on another drive, just in case. Change sda if not drive sda.

Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

More info on sfdisk:
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
See above lnk for info on reading it back in.
sudo sfdisk --no-reread -f /dev/sda -O PT.save < PT.txt

Some have fixed the problem, just by reading the PT.txt file back in or using fdisk to rewrite the table.
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit

Do not write if it is not ok. And you may have to reinstall grub or edit fstab if it has renumbered partitions.

Another way if writing does not work:
Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by ar21 on 2011-05-25
Hi, I am also having a similar problem however I don't seem to figure out how you determined the cylinder boundaries and I've been doing trial and error guessing how to find the numbers in that echo command that fixed the issue.  I was installing a 3rd operating system from a live-usb which fell out during installation and blew a few things away... tried using testdisk but it was also having issues finding the data I wanted off sda2.....

fdisk -lu
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe655e655

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      411647      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          411648   462967167   231277760    7  HPFS/NTFS
/dev/sda3   *   661596160   840640511    89522176   83  Linux
/dev/sda4       840640563   976484072    67921755    f  W95 Ext'd (LBA)
/dev/sda5       840644608   848326639     3841016   82  Linux swap / Solaris
/dev/sda6       848328453   882386172    17028860   82  Linux swap / Solaris

```

sfdisk -d
```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=   409600, Id= 7
/dev/sda2 : start=   411648, size=462555520, Id= 7
/dev/sda3 : start=661596160, size=179044352, Id=83, bootable
/dev/sda4 : start=840640563, size=135843510, Id= f
/dev/sda5 : start=840644608, size=  7682032, Id=82
/dev/sda6 : start=848328453, size= 34057720, Id=82
```

parted /dev/sdaX print returns...

```
# parted /dev/sda1 print
Error: Can't have a partition outside the disk!
```
```
# parted /dev/sda2 print
Model: Unknown (unknown)
Disk /dev/sda2: 237GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  237GB  237GB  ntfs
```

```
# parted /dev/sda4 print
Error: Can't have a partition outside the disk!
```


if someone can demonstrate the math involved in determining cylinder boundaries I'd appreciate it... my googling hasn't turned up an article that articulates it in a way I understand

Thanks in advance for any help!
ar

---

### Post by srs5694 on 2011-05-26
> **ar21 said:**
> Hi, I am also having a similar problem

It's usually best to start your own thread. "Similar problems" often aren't as similar as the person thinks, and trying to solve two unrelated problems in one thread quickly becomes an exercise in frustration for all involved.

I'll reply here simply because this thread has been inactive for several months, so these issues don't seem to be in play.

> however I don't seem to figure out how you determined the cylinder boundaries and I've been doing trial and error guessing how to find the numbers in that echo command that fixed the issue.

Cylinder boundaries are irrelevant and have been for over a decade. Don't worry about them. In fact, partitioning tools have recently switched from aligning partitions on cylinder boundaries to aligning them on 1 MiB (2048-sector) boundaries instead, since doing otherwise degrades performance on some types of modern disks.

> I was installing a 3rd operating system from a live-usb which fell out during installation and blew a few things away... tried using testdisk but it was also having issues finding the data I wanted off sda2.....

TestDisk is good for recovering entire partitions, not individual files. If you want to recover individual files from a damaged partition, use PhotoRec, not TestDisk. If your /dev/sda2 was lost and you're trying to recover it but TestDisk can't find it, then chances are it's so badly damaged you'll never be able to recover anything from it except through PhotoRec or a similar program.

> fdisk -lu
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe655e655

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      411647      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          411648   462967167   231277760    7  HPFS/NTFS
/dev/sda3   *   661596160   840640511    89522176   83  Linux
/dev/sda4       840640563   976484072    67921755    f  W95 Ext'd (LBA)
/dev/sda5       840644608   848326639     3841016   82  Linux swap / Solaris
/dev/sda6       848328453   882386172    17028860   82  Linux swap / Solaris

```sfdisk -d


I don't see anything wrong with your partition table, although I might be missing something.

---

### Post by psusi on 2011-05-26
You are asking parted to look for a partition table inside a partition, which is nonsense.

---

### Post by ploukop on 2011-12-04
I have the same proplem like post #1.
ploukop@panos-laptop:~$ sudo fdisk -lu
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3a18cf96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    90076454    45038196   af  HFS / HFS+
/dev/sda2        90076455   468519659   189221602+   7  HPFS/NTFS/exFAT
/dev/sda3       468520960   476358655     3918848   82  Linux swap / Solaris
/dev/sda4       476359380   976784129   250212375    5  Extended
/dev/sda5       476359443   551190149    37415353+  83  Linux
/dev/sda6       551190213   552025529      417658+   7  HPFS/NTFS/exFAT
/dev/sda7       552025593   642101984    45038196   af  HFS / HFS+
/dev/sda8       642105344   976784129   167339393    7  HPFS/NTFS/exFAT

```
ploukop@panos-laptop:~$ sudo sfdisk -d
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 90076392, Id=af, bootable
/dev/sda2 : start= 90076455, size=378443205, Id= 7
/dev/sda3 : start=468520960, size=  7837696, Id=82
/dev/sda4 : start=476359380, size=500424750, Id= 5
/dev/sda5 : start=476359443, size= 74830707, Id=83
/dev/sda6 : start=551190213, size=   835317, Id= 7
/dev/sda7 : start=552025593, size= 90076392, Id=af
/dev/sda8 : start=642105344, size=334678786, Id= 7

```
ploukop@panos-laptop:~$ sudo parted /dev/sda1 print
```
Model: Unknown (unknown)
Disk /dev/sda1: 46,1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0,00B  46,1GB  46,1GB  hfs+

```
ploukop@panos-laptop:~$ sudo parted /dev/sda2 print
```
Model: Unknown (unknown)
Disk /dev/sda2: 194GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0,00B  194GB  194GB  ntfs

```
ploukop@panos-laptop:~$ sudo parted /dev/sda3 print
```
Model: Unknown (unknown)
Disk /dev/sda3: 4013MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0,00B  4013MB  4013MB  linux-swap(v1)

```
ploukop@panos-laptop:~$ sudo parted /dev/sda4 print
```
Error: Can't have a partition outside the disk! 
```
ploukop@panos-laptop:~$ sudo parted /dev/sda5 print
```
Model: Unknown (unknown)
Disk /dev/sda5: 38,3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags

```
ploukop@panos-laptop:~$ sudo parted /dev/sda6 print
```
Model: Unknown (unknown)
Disk /dev/sda6: 428MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0,00B  428MB  428MB  ntfs

```
ploukop@panos-laptop:~$ sudo parted /dev/sda7 print
```
Model: Unknown (unknown)
Disk /dev/sda7: 46,1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0,00B  46,1GB  46,1GB  hfs+

```
ploukop@panos-laptop:~$ sudo parted /dev/sda8 print
```
Model: Unknown (unknown)
Disk /dev/sda8: 171GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0,00B  171GB  171GB  ntfs

```

Can you help me with my problem?
Sorry for my english, it's not my native language!

---


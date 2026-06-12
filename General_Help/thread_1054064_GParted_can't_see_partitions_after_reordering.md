---
title: "GParted can't see partitions after reordering"
date: 2009-01-29
forum: General Help
---

### Post by Endolith on 2009-01-29
I used SystemRescueCD 1.1.4 to clone my 100 GB drive onto a 160 GB drive.  Then I used GParted 0.4.1 to reorganize and resize the partitions.  

I then used fdisk to fix the partition order, and when I reloaded in GParted it doesn't see any partitions.  It just says "unallocated".

fdisk still sees them, and I am able to boot off the drive and mount the partitions, so I don't understand what the issue is.  

After booting, I run GParted 0.3.8-1ubuntu2 in Ubuntu and it doesn't see the partitions, either.

```
> sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        3921    31455270    7  HPFS/NTFS
/dev/sda3            3922        4379     3678885   db  CP/M / CTOS / ...
/dev/sda4            4380       19457   121114035    f  W95 Ext'd (LBA)
/dev/sda5            4380        4510     1052194+   b  W95 FAT32
/dev/sda6            4511       19196   117965295   83  Linux
/dev/sda7           19197       19457     2096451   82  Linux swap / Solaris
```I guess it's ultimately an issue with parted?

```
> sudo parted
GNU Parted 1.8.9
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Error: Unable to satisfy all constraints on the partition.
```cfdisk gives a more helpful response:

   ```
FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap
                                             Press any key to exit cfdisk
```fdisk expert mode:

```
Expert command (m for help): p

Disk /dev/sda: 255 heads, 63 sectors, 19457 cylinders

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 00   1   1    0 254  63    4         63      80262 de
 2 80   0   1    5 254  63 1023      80325   62910540 07
 3 00 254  63 1023 254  63 1023   62990865    7357770 db
 4 00 254  63 1023 254  63 1023   70348635  242228070 0f
 5 00 254  63 1023 254  63 1023        126    2104389 0b
 6 00 254  63 1023 254  63 1023    2104514  235930590 83
 7 00 254  63 1023 254  63 1023         63    4192902 82
```and sfdisk:

```
> sudo sfdisk -l

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+      4       5-     40131   de  Dell Utility
/dev/sda2   *      5    3920    3916   31455270    7  HPFS/NTFS
/dev/sda3       3921    4378     458    3678885   db  CP/M / CTOS / ...
/dev/sda4       4379   19456   15078  121114035    f  W95 Ext'd (LBA)
/dev/sda5       4379+   4509     131-   1052194+   b  W95 FAT32
/dev/sda6       4510   19195   14686  117965295   83  Linux
/dev/sda7      19196+  19456     261-   2096451   82  Linux swap / Solaris
```

---

### Post by caljohnsmith on 2009-01-29
Please post the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
That will display the output in sectors which is more useful than cylinders when trying to determine problems with the partition table. :)

---

### Post by Endolith on 2009-01-29
> **caljohnsmith said:**
> Please post the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```That will display the output in sectors which is more useful than cylinders when trying to determine problems with the partition table. :)

Thanks.

```
> sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       80325    62990864    31455270    7  HPFS/NTFS
/dev/sda3        62990865    70348634     3678885   db  CP/M / CTOS / ...
/dev/sda4        70348635   312576704   121114035    f  W95 Ext'd (LBA)
/dev/sda5        70348761    72453149     1052194+   b  W95 FAT32
/dev/sda6        72453150   308383739   117965295   83  Linux
/dev/sda7       308383803   312576704     2096451   82  Linux swap / Solaris

``````
> sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=    80262, Id=de
/dev/sda2 : start=    80325, size= 62910540, Id= 7, bootable
/dev/sda3 : start= 62990865, size=  7357770, Id=db
/dev/sda4 : start= 70348635, size=242228070, Id= f
/dev/sda5 : start= 70348761, size=  2104389, Id= b
/dev/sda6 : start= 72453150, size=235930590, Id=83
/dev/sda7 : start=308383803, size=  4192902, Id=82


```

---

### Post by caljohnsmith on 2009-01-29
> **Endolith said:**
> 
```
> sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       80325    62990864    31455270    7  HPFS/NTFS
/dev/sda3        62990865    70348634     3678885   db  CP/M / CTOS / ...
/dev/sda4        70348635   312576704   121114035    f  W95 Ext'd (LBA)
/dev/sda5        70348761    [COLOR="Red"]72453149[/COLOR]     1052194+   b  W95 FAT32
/dev/sda6        [COLOR="Red"]72453150[/COLOR]   308383739   117965295   83  Linux
/dev/sda7       308383803   312576704     2096451   82  Linux swap / Solaris

```
Note that your sda6 logical partition begins at the sector immediately after the end of the sda5 logical partition; that's what parted/gparted is complaining about, because for sda6 to be a logical partition, it needs to have an EBR (Extended Boot Record) that comes right before the logical partition (or at least it needs to in order to be compatible with the standard that most partition programs use), and usually the EBR is 63 sectors (1 track) before the start of the logical partition. I think the easiest solution to fix your problem would be to shrink the sda5 FAT partition by just 63 sectors (32 KB) to make room for the EBR. First try:
```
sudo mount /dev/sda5 /mnt && ls -l /mnt
```
That's just to make sure your sda5 partition is mountable and readable, so check that you can see the root directory of sda5 with the above command. If you can, proceed with:
```
sudo umount /dev/sda5 /dev/sda5

```
Note the double "/dev/sda5" is not a typo, it is just in case sda5 is mounted more than once somewhere; you don't want to resize sda5 if sda5 is mounted anywhere. Next do:
```
[ "$(mount | grep sda5)" ] || sudo fatresize -s 1077414912 /dev/sda5
```
The first part of the command tests whether sda5 is mounted anywhere, and only if sda5 is not mounted will the fatresize command be executed. Please post the output of that command, and we can work from there.

---

### Post by Endolith on 2009-01-29
> **caljohnsmith said:**
> First try:
```
sudo mount /dev/sda5 /mnt && ls -l /mnt
```That's just to make sure your sda5 partition is mountable and readable

As I said, all the partitions are already mounted and readable.

> Next do:
```
[ "$(mount | grep sda5)" ] || sudo fatresize -s 1077414912 /dev/sda5
```The first part of the command tests whether sda5 is mounted anywhere, and only if sda5 is not mounted will the fatresize command be executed. Please post the output of that command, and we can work from there.Hmmm... that doesn't work:

```
$ [ "$(mount | grep sda5)" ] || sudo fatresize -s 1077414912 /dev/sda5
fatresize 1.0.2 (07/11/08)
Error: Unable to satisfy all constraints on the partition.

```

---

### Post by caljohnsmith on 2009-01-29
How about posting the output of:
```
sudo fatresize -i /dev/sda5
```

---

### Post by Endolith on 2009-01-29
> **caljohnsmith said:**
> How about posting the output of:
```
sudo fatresize -i /dev/sda5
```

Same.

```
> sudo fatresize -i /dev/sda5
fatresize 1.0.2 (07/11/08)
Error: Unable to satisfy all constraints on the partition.

```

Does it do some kind of parted check first?

---

### Post by caljohnsmith on 2009-01-29
I'll have to do some experimenting on one of my own drives to figure out why fatresize might be returning that error still, but since it is only a 1 GB partition, what would you think of just backing up the contents of sda5, delete sda5, and then you can create and format a new sda5 FAT partition with the correct start/stop points? I think that would work. If you want to do that, you can delete sda5 with the following command:
```
echo '0,0,0' | sudo sfdisk --no-reread -fuS /dev/sda -N5 -O ~/Desktop/sda_sectors_modified.save
```
That will also create a "sda_sectors_modified.save" file that will contain the sectors on the HDD that are modified by the above command, so if for some reason anything were to go wrong, we can easily restore your original partition table with that file. Therefore, it would be good to save that file. Once you delete sda5, you should be able to use gparted to create a new FAT logical partition in that space, because your partition table should be OK at that point. Let me know how that goes or if you run into problems again.

---

### Post by Endolith on 2009-01-29
> **caljohnsmith said:**
> I'll have to do some experimenting on one of my own drives to figure out why fatresize might be returning that error still, but since it is only a 1 GB partition, what would you think of just backing up the contents of sda5

I still have the original on the other drive. :)

> If you want to do that, you can delete sda5 with the following command:
```
echo '0,0,0' | sudo sfdisk --no-reread -fuS /dev/sda -N5 -O ~/Desktop/sda_sectors_modified.save
```That will also create a "sda_sectors_modified.save" file that will contain the sectors on the HDD that are modified by the above command, so if for some reason anything were to go wrong, we can easily restore your original partition table with that file. Therefore, it would be good to save that file. Once you delete sda5, you should be able to use gparted to create a new FAT logical partition in that space, because your partition table should be OK at that point. Let me know how that goes or if you run into problems again.now parted works again 

```
> sudo parted
GNU Parted 1.8.9
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: ATA ST9160821A (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16
 2      41.1MB  32.3GB  32.2GB  primary   ntfs         boot
 3      32.3GB  36.0GB  3767MB  primary   fat32
 4      36.0GB  160GB   124GB   extended               lba
 5      37.1GB  158GB   121GB   logical   ext3
 6      158GB   160GB   2147MB  logical   linux-swap
```I'll try to recreate the partition when I'm actually sitting in front of the computer.

Thanks!

---

### Post by caljohnsmith on 2009-01-29
That's great, as long as parted is happy, your partition table should be fine now. Keep me posted how things go, but it sounds like you should be OK now that your partition table doesn't have that offending partition. :)

---

### Post by Endolith on 2009-01-29
So I added the new FAT partition and Gparted saw it fine, but then i ran cfdisk and it still complains.  

```
FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap
```So then I stupidly shrunk the partitions to make space between them, and now I have to wait many hours while it does that.  :)

If I re-stretch them back to the size I want with GParted and "lock to cylinders" on, shouldn't it do it right?  It seems odd that GParted would resize partitions in a way that it cannot read later.

---

### Post by caljohnsmith on 2009-01-29
> **Endolith said:**
> So I added the new FAT partition and Gparted saw it fine, but then i ran cfdisk and it still complains.  

```
FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap
```So then I stupidly shrunk the partitions to make space between them, and now I have to wait for two hours while it does that.  :)

If I re-stretch them back to the size I want with GParted and "lock to cylinders" on, shouldn't it do it right?  It seems odd that GParted would resize partitions in a way that it cannot read later.
In my experience, you can't trust what "cfdisk" says, so I don't think your partition table is necessarily corrupt again. If you use the "lock to cylinders" option in gparted, I think you should be fine. If you have any problems, please post "sudo fdisk -lu" again, because analyzing it's output will give a more accurate idea of whether your partition table is still a problem.

---

### Post by Endolith on 2009-01-30
Alright.  I got it into a configuration that even cfdisk is happy with:

```
~> sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       80325    62990864    31455270    7  HPFS/NTFS
/dev/sda3        62990865    70348634     3678885   db  CP/M / CTOS / ...
/dev/sda4        70348635   312576704   121114035    f  W95 Ext'd (LBA)
/dev/sda5        70348698    72453149     1052226    b  W95 FAT32
/dev/sda6        72453213   308383739   117965263+  83  Linux
/dev/sda7       308383803   312576704     2096451   82  Linux swap / Solaris

```

Thanks!

---

### Post by caljohnsmith on 2009-01-30
That's great news, your partition table looks totally OK now. I just wanted to mention that cfdisk gives the exact same error for my HDD as what you got before:
```
FATAL ERROR: Bad logical partition 7: enlarged logical partitions overlap
```
And yet fdisk, sfdisk, parted, etc do not complain about my HDD; I've even looked at the raw data in the MBR (Master Boot Record) and EBRs (Extended Boot Records), and I can't find anything wrong with my partition table other than my logical partitions are not in physical order (but there's nothing wrong with that). But I think not having the logical partitions in physical order is what is causing cfdisk to choke at least with my HDD, because there are actually two different standards for how to set up extended partitions; one of the standards does not allow the logical partitions to be in arbitrary order, so that's what cfdisk probably uses. Anyway, cheers and hope you don't run into any more partition table problems. :)

---


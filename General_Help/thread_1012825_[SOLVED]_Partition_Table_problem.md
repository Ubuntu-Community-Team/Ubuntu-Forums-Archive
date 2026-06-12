---
title: "[SOLVED] Partition Table problem"
date: 2008-12-16
forum: General Help
---

### Post by eotakos on 2008-12-16
Hi! - I used testdisk to undelete linux partitions, and it did just that! - unfortunately, now the vista's ntfs is inconsistent and it seems that it is a partition table problem (one that testdisk can't fix). I can't manipulate the ntfs partition in any way with gparted - the message i get when i try to check it looks like this : 

```
$MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
Failed to startup volume: Input/output error.
ERROR(5): Opening '/dev/sda2' as NTFS failed: Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.
```

but the thing is that i can't get into windows in order to do a chkdsk...

trying ntfsfix gives the following result:

```
Mounting volume... $MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
Failed to startup volume: Input/output error.
FAILED
Attempting to correct errors... $MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
FAILED
Failed to startup volume: Input/output error.
Volume is corrupt. You should run chkdsk.
```

if i try to repair the installation from windows media, the cd recovery program at some point will prompt me to choose the partition (with the installation) that is to be repaired, but nothing is listed below. So, the recovery program just won't see the partition...

any suggestions?

thanks in advance

---

### Post by caljohnsmith on 2008-12-16
Are you sure you recovered the correct NTFS partition for Vista? How about posting the output of the following:
```
sudo sfdisk -l
sudo fdisk -lu
sudo parted /dev/sda print
```
Then run testdisk again and post the results of the "deep search" as follows:
[B]
If you are using Version 6.8:[/B]
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results.
[B]
If you are using Version 6.9:[/B]
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results.

---

### Post by eotakos on 2008-12-16
first of all thanks for answering!

from the parts below, the sda2 is the one with the problem.

sudo sfdisk -l  :

```

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+   1530-   1531-  12291072   27  Unknown
/dev/sda2   *   1530+  12595-  11065-  88879608+   7  HPFS/NTFS
/dev/sda3      12596+  38912   26317- 211391271    f  W95 Ext'd (LBA)
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      12596+  28115-  15520- 124664336   83  Linux
/dev/sda6      28116+  32093-   3978-  31953252   83  Linux
/dev/sda7      32094+  38386-   6293-  50548488   83  Linux
/dev/sda8      38387   38912-    526-   4225084   82  Linux swap / Solaris

```


sudo fdisk -lu : 
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    24584191    12291072   27  Unknown
/dev/sda2   *    24584192   202343408    88879608+   7  HPFS/NTFS
/dev/sda3       202354803   625137344   211391271    f  W95 Ext'd (LBA)
/dev/sda5       202354866   451683537   124664336   83  Linux
/dev/sda6       451683603   515590106    31953252   83  Linux
/dev/sda7       515590173   616687148    50548488   83  Linux
/dev/sda8       616687155   625137322     4225084   82  Linux swap / Solaris

```


and 

sudo parted /dev/sda print : 
```

Model: ATA TOSHIBA MK3252GS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  12.6GB  12.6GB  primary   ntfs              
 2      12.6GB  104GB   91.0GB  primary   ntfs         boot 
 3      104GB   320GB   216GB   extended               lba  
 5      104GB   231GB   128GB   logical   ext3              
 6      231GB   264GB   32.7GB  logical   ext3              
 7      264GB   316GB   51.8GB  logical   ext3              
 8      316GB   320GB   4326MB  logical   linux-swap    
```    


as far as the testdisk is concerned, i used the 6.10 version ( i don't know if this affects anything). what i did (prior to this message) was this : 
I did everything up to the analyze thing, then i changed the type of the partitions according to that it was supposed to be, and then i hit write. One time i did the deep search but the output was way to many partitions than these that i really have; so (despite) all the time dedicated to deep search i hit cancel and exit....

anyway i'm doing this all over again in order to post the results. the quick search is easy and i'm giving it right away, but the other one will take some time....

---

### Post by eotakos on 2008-12-16
1st and 2nd testdisk screens

but (oups!) it didn't ask me if i have any vista partitions...

---

### Post by eotakos on 2008-12-16
here i have 2 more screenshots of testdisk attached.
Strange thing - it says that a linux partition can't be recovered, while there's no linux partition missing... (3rd screenshot)

the 4th screenshot is that with the thorough search - as i mentioned above - way too many partitions....

any suggestions?

---

### Post by eotakos on 2008-12-16
yei! i did it ! 

note to anyone reading this because of having resembling problems:

for every partition testdisk displays with the quick analyze, you should press "p" to see whether it can display the contents. if it can, then everything is ok and you should mark it as primary or logical or whatever it was (before the errors). If it can't, notice the starting and ending sectors; they must be overlaping and this should be the issue. 

Do the thorough search! after  the search is complete ( it takes some time), it is most likely that all desplayed results (partitions) will be marked as deleted. This is not a faulty situation - testdisk displays partitions like this, so that you go and check each and every one of them (pressing p) to see if it can display the contents. The ones that can't display the contents leave them as deleted, the correct ones mark them as the type they are supposed to be. then write results to the partition table and restart.

IF you don't know what was the type of the partition prior to the errors, you can consult the documentation (which you should anyway :-) )  there are some tips there.

general documentation with examples:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

tips for telling which is what : 
[http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical](http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical)


caljohnsmith thank you again for taking the time to post here. you maybe didn't solve the issue for me, but you kept me trying.

---

### Post by caljohnsmith on 2008-12-16
I was just typing my reply to you about using "P" to list the directories and find the correct NTFS partition, so I'm glad you figured it out on your own. Let me know if you have any more problems about your partition table, but it sounds like you figured out the correct one. :)

---

### Post by eotakos on 2008-12-16
Funny thing! - everything works, but now gparted doesn't recognize any of the partitions on the hard drive. any ideas on this one?

i did enough studying for today, that will be the homework for tomorrow :-)

---

### Post by caljohnsmith on 2008-12-16
> **eotakos said:**
> Funny thing! - everything works, but now gparted doesn't recognize any of the partitions on the hard drive. any ideas on this one?

i did enough studying for today, that will be the homework for tomorrow :-)
I've seen where testdisk sometimes creates an extended partition that exceeds the end point of the last logical partition, and if the extended partition ends at the end of the HDD like in your case, the extended partition can exceed the ending sector of the HDD. That causes problems obviously with gparted, so it would be good to check if that happened to you. How about posting the new output of:
```
sudo fdisk -lu
sudo sfdisk -d /dev/sda
sudo parted /dev/sda print
```
And we can work from there.

---

### Post by eotakos on 2008-12-16
sudo fdisk -lu

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x438c7787

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    24584191    12291072    7  HPFS/NTFS
/dev/sda2   *    24595515   202354731    88879608+   7  HPFS/NTFS
/dev/sda3       202354740   625153409   211399335    f  W95 Ext'd (LBA)
/dev/sda5       202354866   451683537   124664336   83  Linux
/dev/sda6       451683603   515590106    31953252   83  Linux
/dev/sda7       515590173   616687148    50548488   83  Linux

```


sudo sfdisk -l

```
Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+   1530-   1531-  12291072    7  HPFS/NTFS
/dev/sda2   *   1531   12595-  11065-  88879608+   7  HPFS/NTFS
/dev/sda3      12596   38913   26318  211399335    f  W95 Ext'd (LBA)
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      12596+  28115-  15520- 124664336   83  Linux
/dev/sda6      28116+  32093-   3978-  31953252   83  Linux
/dev/sda7      32094+  38386-   6293-  50548488   83  Linux

```


sudo parted /dev/sda print
```

Error: Can't have a partition outside the disk!    
```

seems like your guess was right!

i don't know if this really means anything, but have a look at the 3rd screenshot of testidisk: the 3rd "paragraph" reads 
> the hard disk ...  seems too small!


i'm starting to getting the big picture - and now i have a hint about what i must have done wrong with the recovery: i chose the extended partition to take up all the remaining space... but i did that only because i wanted it to include the swap partition. As you can see from the later results, there is no swap. i didn't let testdisk to recover the swap, because it wouldn't let me recover it as logical part (which it was prior to the recovery). 

So i intended to make a swap within the extended partition after the recovery using gparted... i run the program, and surprise! "unallocated 298 Gib"  ...    and here we are :-)

again! thank you very much for your time!!!

---

### Post by caljohnsmith on 2008-12-16
Yes, unfortunately it does look like your extended partition runs off the end of your HDD. :) But to correct it, please post the sfdisk command, but note that it uses "-d":
```
sudo sfdisk -d /dev/sda

```
I would rather not have to do the math to create what sfdisk will give us with that above command, and we will need that to fix your partition table.

---

### Post by eotakos on 2008-12-17
Oups! it seems like i wasn't paying much attention, and i thought they were the same commands. Up to now i've used only the fdisk command for data concerning the partitions. The others are new to me, so i wouldn't know the difference. Sorry about that!

here is the output i get

sudo sfdisk -d /dev/sda:

```
unit: sectors

/dev/sda1 : start=     2048, size= 24582144, Id= 7
/dev/sda2 : start= 24595515, size=177759217, Id= 7, bootable
/dev/sda3 : start=202354740, size=422798670, Id= f
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=202354866, size=249328672, Id=83
/dev/sda6 : start=451683603, size= 63906504, Id=83
/dev/sda7 : start=515590173, size=101096976, Id=83

```

hm... i see where this is going... so i guess now we have to correct that table, and then use it as input back to the sfdisk command, like so

 % sfdisk /dev/hda < hda.out

as stated at the sfdisk man page...  but what is it that has to be corrected...? all these different units (the cylinders, the sectors, etc) seem to confuse me still

---

### Post by caljohnsmith on 2008-12-17
```
unit: sectors

/dev/sda1 : start=     2048, size= 24582144, Id= 7
/dev/sda2 : start= 24595515, size=177759217, Id= 7, bootable
/dev/sda3 : start=202354740, size=[COLOR="Red"]414332409[/COLOR], Id= f
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=202354866, size=249328672, Id=83
/dev/sda6 : start=451683603, size= 63906504, Id=83
/dev/sda7 : start=515590173, size=101096976, Id=83
```
OK, the partition table above should correct your extended partition problem; I modified your partition table as shown above so that the extended partition will end at the end of sda7, and not end on a sector that is beyond the end of the HDD. How about downloading the attached "partition_table.txt" to your desktop and do:
```
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
```
And then I think you should be all set. It would be a good idea to reboot and then post the new output of "sudo fdisk -lu" so we can make sure everything went OK. Let me know how it goes. :)

---

### Post by eotakos on 2008-12-17
actually i took the liberty to alter this a little bit, so that the extended partition reaches to the end of the hard disk (i need the swap part...). To do this i used the number of the total sectors as shown at the result of the sudo fdisk -lu command (at the top)

now, my partition table looks like this:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x438c7787

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    24584191    12291072    7  HPFS/NTFS
/dev/sda2   *    24595515   202354731    88879608+   7  HPFS/NTFS
/dev/sda3       202354740   625142447   211393854    f  W95 Ext'd (LBA)
/dev/sda5       202354866   451683537   124664336   83  Linux
/dev/sda6       451683603   515590106    31953252   83  Linux
/dev/sda7       515590173   616687148    50548488   83  Linux

```

and gparted shows everything as is should be. All i need to do now is to add the swap partition.

Case closed!

Thank you very very much once again my friend. I have to say that you are a member of the ubuntu community to look up to.

---

### Post by caljohnsmith on 2008-12-17
I'm really glad that worked, and also having the extended partition end at the end of the drive is certainly a good idea since you are planning on adding a swap partition. I learned that sfdisk trick of manually writing the partition table from forum member meierfra, so you can give him credit for that. Anyway, cheers and have fun with your OSes. :)

---

### Post by blade2008 on 2011-02-01
Hi I am trying to fix my windows vista partition. I dont know which partition should be primary, logical and which should be the bootable. I have only 2 NTFS partition one is C: which is approx 245 GB big and one is D: (Data) which is 217 GB big. One is PQService which is a hidden Acer Partition. and 27 GB are not allocated. Now which partition should I set Primary and bootable in testdisk.

Here are my fdisk and sfdisk outputs before doing anything with testdisk: 

[PHP]ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA WDC WD5000AAJS-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  10.5GB  10.5GB  primary  ntfs
 2      10.5GB  255GB   245GB   primary  ntfs         boot
 3      282GB   500GB   218GB   primary  ntfs

ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+   1273    1274-  10233373+   7  HPFS/NTFS
/dev/sda2   *   1274   31005   29732  238822290    7  HPFS/NTFS
/dev/sda3      34322+  60801-  26479- 212691968    7  HPFS/NTFS
/dev/sda4          0       -       0          0    0  Empty
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa0af63ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+   7  HPFS/NTFS
/dev/sda2   *        1275       31006   238822290    7  HPFS/NTFS
/dev/sda3           34323       60802   212691968    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
[/PHP]

And here is my testdisk after depth search:

[PHP]TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  1273 254 63   20466747 [PQSERVICE]
D HPFS - NTFS           1274   0  1 31005 254 63  477644580
D HPFS - NTFS           1274  14 21 34322  34  8  530917368
D HPFS - NTFS           1274  14 21 60801  47 46  956303360
D HPFS - NTFS          34322  34 17 60801  15 14  425383936 [Data]
D Linux Swap           59666   1  1 60800 254 47   18233696
D HPFS - NTFS          60738   0  1 60800 254 63    1012095 [ACER_SERVIC]



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 10478 MB / 9993 MiB


[/PHP]

I hope somebody can help me.

---

### Post by srs5694 on 2011-02-01
> **blade2008 said:**
> Hi I am trying to fix my windows vista partition.

First, it's usually best to start a new thread for your own problem rather than hijack an existing one (even one that's marked as "solved" and no longer being posted to).

Second, what's wrong with your Vista partition? You don't specify, and I don't see anything obviously wrong in your current partition table, except that there's a bit of unused space between /dev/sda2 and /dev/sda3. Have you lost or accidentally deleted a partition?

Third and finally, I see no evidence of any Ubuntu installation on this disc. It appears that this is a Windows-only setup. If so, you're more likely to get helpful responses on a Windows forum.

---


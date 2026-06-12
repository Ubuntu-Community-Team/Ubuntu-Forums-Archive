---
title: "Problem with gparted"
date: 2008-12-22
forum: General Help
---

### Post by N4zgu1 on 2008-12-22
Gparted doesnt recognize any of my partitions, it says that all my hardrive is empty (unallocated). But I am shure it is not.

I have 7 partitions: 
4 Windows partitions


3 Linux partitions:
-1 root partition
-1 /home partition 
-1 swap

I have tried to run Gparted form my OS (dremlinux 3.0) and from two different live cds: dremlinux and LinuxMint

I have a Dell inspiron 1525 and Im running dreamlinux 3.0

Can somebody help me??????

---

### Post by LoneWolfJack on 2008-12-22
can you please post the output of

```
sudo fdisk -lu
```

---

### Post by N4zgu1 on 2008-12-22
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98229822

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   483155968   488394751     2619392    c  W95 FAT32 (LBA)
/dev/sda2           81920    20561919    10240000    7  HPFS/NTFS
/dev/sda3   *    20563200   125419454    52428127+   7  HPFS/NTFS
/dev/sda4       125419579   488394751   181487586+   f  W95 Ext'd (LBA)
/dev/sda5       483155968   488394751     2619392   dd  Unknown
/dev/sda6       125419581   137420009     6000214+  83  Linux
/dev/sda7       137420073   149420564     6000246   82  Linux swap / Solaris
/dev/sda8       149420628   483154874   166867123+  83  Linux

Partition table entries are not in disk order

---

### Post by caljohnsmith on 2008-12-22
> **N4zgu1 said:**
> 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   [COLOR="Red"]483155968[/COLOR]   488394751     2619392    c  W95 FAT32 (LBA)
/dev/sda2           81920    20561919    10240000    7  HPFS/NTFS
/dev/sda3   *    20563200   125419454    52428127+   7  HPFS/NTFS
/dev/sda4       125419579   [COLOR="Red"]488394751[/COLOR]   181487586+   f  W95 Ext'd (LBA)
/dev/sda5       483155968   488394751     2619392   dd  Unknown
/dev/sda6       125419581   137420009     6000214+  83  Linux
/dev/sda7       137420073   149420564     6000246   82  Linux swap / Solaris
/dev/sda8       149420628   483154874   166867123+  83  Linux

It looks like the problem is your partition table is corrupted for some reason; your sda1 partition actually falls within the boundaries of the extended partition, which it shouldn't since sda1 is a primary partition. Also, do you know what is on your sda5 partition? Currently the file system type is marked as "unknown". How about also posting:
```
sudo sfdisk -d /dev/sda
```
I think your best bet would be to use testdisk to recover your partition table, so if that sounds good to you, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
**If you are using Version 6.8:**
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results.

**If you are using Version 6.9:**
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results.

---

### Post by N4zgu1 on 2008-12-22
here is the output of sudo sfdisk -d /dev/sda

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=483155968, size=  5238784, Id= c, bootable
/dev/sda2 : start=    81920, size= 20480000, Id= 7
/dev/sda3 : start= 20563200, size=104856255, Id= 7, bootable
/dev/sda4 : start=125419579, size=362975173, Id= f
/dev/sda5 : start=483155968, size=  5238784, Id=dd
/dev/sda6 : start=125419581, size= 12000429, Id=83
/dev/sda7 : start=137420073, size= 12000492, Id=82
/dev/sda8 : start=149420628, size=333734247, Id=83

---

### Post by meierfra. on 2008-12-22
deleted

---

### Post by LoneWolfJack on 2008-12-22
like caljohnsmith posted, your partition table looks odd... 

you may have some luck with using gparted to move some partitions back and forth, but chances are, at some point you'll end up with a totally unusable partition table.

I'd recommend backing up your data and reformatting your drive.

---

### Post by meierfra. on 2008-12-22
deleted

---

### Post by Vantrax on 2008-12-22
There are a few very complex ways to try and resolve your issues, but the only safe way is to back up your data and reinstall.

Either way you have some corruption and will need to fix it. I would try backing up your data and attempting to use a tool to restore the partition table first. Testdisk would be a good option or if you prefer windows style appts I think ParitionMagic has a tool that can do that.

You could try to do a copy (dd) of each partition cleanly onto another disk with the partitions already created then just set grub back up and set the windows disk to active manually and put a windows disk in and run fixMBR (or just use grub).

---

### Post by LoneWolfJack on 2008-12-22
> There is a good chance that testdisk can fix your partition table, so no reason to reformat. Just follow caljohnsmiths advice. 

I find this comment both, unhelpful and insulting. First, only illiterates start fiddling with their partitions without pulling a complete backup. Second, you shouldn't come here telling people not to take into consideration "some other guy's" recommendation on the basis of "my solution could be better".

N4zgu1, let me make that clear, you should absolutely try testdisk if you're short on time and after pulling a backup. still, I'd recommend reinstalling. partition tables don't go awkward without a reason. testdisk  may just cure the symptoms.

---

### Post by dummyhead3 on 2008-12-22
I would try to defragment your windows drives.

---

### Post by N4zgu1 on 2008-12-22
It may be useful if I explain why my partition table is a mess.

I am a noob in linux first I tried ubuntu in my last laptop and I liked it .

But when I got this laptop (Dell inspiron 1525) a friend told me about Dreamlinux so I gave it a try. 

My laptop came with Vista preinstalled:
1 partition for Vista
1 partition for Media Direct
1 partition for Recovery

I resized the Vista partition and I installed Dreamlinux:
1 partition for /
1 partition for /home
1 partition for swap

Everything was working fine until I decided to update all my packages with Synaptic.  After doing so All my system broke up and I had 2 extra options in the Grub (debian ????).

So I decided to reinstall Dreamlinux, this time the xfce version but things got worse I couldnt even run it. Since I needed my laptop and I didnt have time to download another Distro I decided to reinstall the Gnome Version (this time I didnt update it). After that I realized that I couldnt boot Vista anymore but the extra options dissapered)

After a week working only with Dreamlinux I realized that I had a second Media direct (i dont know where it came from).

I downloaded LinuxMint and when I tried to install it (and replace Dreamlinux) But Gparted didnt recognized any of my partitions.

Thats all the story

* I made all the partitions with the Dreamlinux live cd following the instructions of the wiki 

* I dont care about the information in any partition except from the /home partition

---

### Post by caljohnsmith on 2008-12-22
I think there is a good chance we can recover your correct partition structure with testdisk if you want to give it a try. Or like you say, you could save everything from your /home partition and reinstall linux, but you would first have to delete the offending partitions so your partition table isn't corrupt. That's the only way you could reinstall I think, because it is likely that the linux installer will see the HDD as unallocated since your partition table is definitely corrupt. It's up to you what you want to do, but if you would like my help recovering your correct partition table, then please post the results of the deep scan search from testdisk. :)

EDIT: Please also post the output of:
```
sudo sfdisk -l
```

---

### Post by N4zgu1 on 2008-12-22
Here is the output of "analyze"

```


Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * FAT32 LBA            30075  17 23 30401  42 41    5238784 [MEDIADIRECT]
 2 P HPFS - NTFS              5  25 21  1279 234 43   20480000 [RECOVERY]
 3 * HPFS - NTFS           1280   0  1  7806 254 63  104856255 [OS]
 4 E extended LBA          7807   1 62 30401  42 41  362975173
Only one partition must be bootable
Space conflict between the following two partitions
 4 E extended LBA          7807   1 62 30401  42 41  362975173
 1 * FAT32 LBA            30075  17 23 30401  42 41    5238784 [MEDIADIRECT]
 5 L Sys=DD               30075  17 23 30401  42 41    5238784
   X extended              7807   1 63  8553 254 63   12000430
 6 L Linux                 7807   2  1  8553 254 63   12000429 [Dreamlinux]
   X extended              8554   0  1  9300 254 63   12000555
 7 L Linux Swap            8554   1  1  9300 254 63   12000492
    Next
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition






```


Im doing the deepsearch

---

### Post by N4zgu1 on 2008-12-22
here is the output of sfdisk -l


```
Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *  30075+  30401-    327-   2619392    c  W95 FAT32 (LBA)
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda2          5+   1279-   1275-  10240000    7  HPFS/NTFS
/dev/sda3   *   1280    7806    6527   52428127+   7  HPFS/NTFS
/dev/sda4       7807+  30401-  22595- 181487586+   f  W95 Ext'd (LBA)
/dev/sda5      30075+  30401-    327-   2619392   dd  Unknown
/dev/sda6       7807+   8553     747-   6000214+  83  Linux
/dev/sda7       8554+   9300     747-   6000246   82  Linux swap / Solaris
/dev/sda8       9301+  30074   20774- 166867123+  83  Linux

```

---

### Post by N4zgu1 on 2008-12-22
Here is the output


```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     4 254 60      80259 [DellUtility]
P HPFS - NTFS              5  25 21  1279 234 43   20480000 [RECOVERY]
D HPFS - NTFS           1279 234 44  7806 234 29  104856241
D HPFS - NTFS           1280   0  1  7806 254 49  104856241 [OS]
D HPFS - NTFS           1280   0 15  7806 254 63  104856241
P Linux                 7807   2  1  8553 254 58   12000424 [Dreamlinux]
L Linux Swap            8554   1  1  9300 254 43   12000472
D Linux                 9301   1  1 30074 254 56  333734240 [Dreamlinux]
D Linux                 9302   2  1 30076   0 56  333734240 [Dreamlinux]
D FAT32 LBA            30075  17 23 30401  42 41    5238784 [MEDIADIRECT]



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, 41 MB / 39 MiB
```

---

### Post by N4zgu1 on 2008-12-22
It seems that there are two options that correspond to the size of my /home but test disk doesnt accept both at the same time how do I know which is the rigth one????????

---

### Post by caljohnsmith on 2008-12-22
> **N4zgu1 said:**
> 
```

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]D[/COLOR] FAT16 >32M               0   1  1     4 254 60      80259 [DellUtility]
[COLOR="Red"]P[/COLOR] HPFS - NTFS              5  25 21  1279 234 43   20480000 [RECOVERY]
[COLOR="Red"]D[/COLOR] HPFS - NTFS           1279 234 44  7806 234 29  104856241
[COLOR="Red"]*[/COLOR] HPFS - NTFS           1280   0  1  7806 254 49  104856241 [OS]
[COLOR="Red"]D[/COLOR] HPFS - NTFS           1280   0 15  7806 254 63  104856241
[COLOR="Red"]L[/COLOR] Linux                 7807   2  1  8553 254 58   12000424 [Dreamlinux]
[COLOR="Red"]L[/COLOR] Linux Swap            8554   1  1  9300 254 43   12000472
[COLOR="Red"]L[/COLOR] Linux                 9301   1  1 30074 254 56  333734240 [Dreamlinux]
[COLOR="Red"]D[/COLOR] Linux                 9302   2  1 30076   0 56  333734240 [Dreamlinux]
[COLOR="Red"]P[/COLOR] FAT32 LBA            30075  17 23 30401  42 41    5238784 [MEDIADIRECT]
```

OK, as has all ready been discussed, it would be best if you first back up all your important data, especially in your home partition since you mentioned that. Next, use the up/down arrows to select each partition above, and then use the right/left arrows to mark the partitions as I've highlighted in red. But for the partitions that are marked "P", "*", and "L", press "p" to list their directories. If they all show a directory listing, then those should be your correct partitions. If any of the partitions I've marked above with "P", "*", and "L" do not show a directory listing, do not proceed, but if they do, press enter to get to the next screen where you can write the new partition table. Next reboot, and post the new output of:
```
sudo sfdisk -luS
sudo fdisk -l
sudo sfdisk -V
```
It might be that you won't immediately be able to boot the sda HDD since your partition numbering will change it looks like, but we can fix that too.

---

### Post by unutbu on 2008-12-22
Use the up/down arrows to highlight a partition.
Press 'p' to see a listing of the files in the partition.
This can help you determine which partition is the one you want to keep.

---

### Post by unutbu on 2008-12-22
Hi Caljohnsmith, I've been trying to figure out why you sometimes ask for more than one of these:
```

sudo sfdisk -luS
sudo sfdisk -d
sudo fdisk -lu
```
Do you do it for confirmation of consistency?
Have you ever found them giving conflicting output?
Thanks a lot for your time. I really enjoy learning by watching you solve problems.

---

### Post by N4zgu1 on 2008-12-22
thanks for the help I will do as you say. If you are sure that that is the correct order Ill trust you

---

### Post by caljohnsmith on 2008-12-23
> **unutbu said:**
> Hi Caljohnsmith, I've been trying to figure out why you sometimes ask for more than one of these:
```

sudo sfdisk -luS
sudo sfdisk -d
sudo fdisk -lu
```
Do you do it for confirmation of consistency?
Have you ever found them giving conflicting output?
Thanks a lot for your time. I really enjoy learning by watching you solve problems.
Hi Unutbu, yes, you're right, I do it mainly for confirmation of consistency; I did some experiments where I took a drive and deliberately corrupted the partition table in different ways, and then I ran sfdisk, fdisk, parted, etc on the drive to see what they would say. At least in my experiments (which I won't claim as containing all possible scenarios of a corrupted partition table :)), it looks like "sfdisk -V" reports most partition problems *except* the notorious "omitting empty partition (X)"; at least in my experiments, fdisk was the only command to correctly return that error. I found you can get an "omitting empty partition (X)" error when one of the EBRs (Extended Boot Records) has a blank record for a partition when it shouldn't, meaning one of the other EBRs or the MBR points to that EBR, and yet that EBR is empty (or at least that is one cause of that error message I found). So in order to check whether a drive's partition table is OK, it helps to see the output of more than one of those commands it seems.

Also, I think it helps to see the output with the partition table start/stop points given both in sectors and cylinders; to see the output in sectors is the most helpful, because then you can manually check whether there are any overlapping partitions. In addition, you can check that the logical partitions are separated by a minimum of 64 sectors, because each logical partition must have its own EBR 63 sectors before the beginning of that partition. And as is the case with N4zgu1's partition table, I've found that one should check that none of the primary partitions fall inside or overlap with the extended partition. And lastly, it is always good to check that none of the partition end points exceed the total sectors available on the drive, because that's another partition table problem I've seen in the forums.

But I also like to ask for the output of "fdisk -l" or "sfdisk -l", because then you can directly compare the start/stop points of partitions in cylinders with testdisk's output, because testdisk displays the start/stop points in cylinders instead of sectors. I like "sfdisk -l" the best for that, because it begins counting cylinders starting with 0 just like testdisk does, similar to the LBA (Logical Block Addressing) standard. In other words, if you compare the output of "sfdisk -l", "fdisk -l", and testdisk, you will see that "sfdisk -l" should exactly agree with testdisk about the start/stop points, whereas "fdisk -l" is always +1 cylinder different since it begins counting cylinders with 1 and not 0. Not a big difference, but I think it's nicer when you can compare results that should directly match rather than all being 1 cylinder different.

And lastly, I like to ask the person for the output of "sfdisk -d", because then we have an online backup of their original partition table in a form that is easily restorable; in other words, if they first do the following to make a backup of their partition table:
```
sudo sfdisk -d /dev/sdX > partition_table.txt
```
They can restore their original partition table at any time by simply doing:
```
sudo sfdisk --force /dev/sdX < partition_table.txt
```
So if for some reason they accidentally make their partition table worse with testdisk, they can use the above commands to at least get back to where they started from. I learned that trick from meierfra, and I think it can be extremely useful.

But anyway, that was probably more than you wanted to hear; if you happen to find a better program/command that does a better job reporting all partition table problems, including the empty partition table problem, please let me know. I would imagine that meierfra will find a better way (if he hasn't all ready), so you might want to ask his opinion. :)

---

### Post by unutbu on 2008-12-23
Another beautiful explanation. Thank you so much.

Happy Holidays,
Unutbu

---

### Post by N4zgu1 on 2008-12-23
I made the partition table as you said.

After that I couldnt boot. So I decided to probe with the LinuxMint cd. Finally gparted recognized my partitions and I installed LinuxMint. Everything is fine until now.

Here is the output of sudo sfdisk -luS


```
Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1         81920  20561919   20480000   7  HPFS/NTFS
/dev/sda2      20563200 125419440  104856241   7  HPFS/NTFS
/dev/sda3     125419455 483154874  357735420   f  W95 Ext'd (LBA)
/dev/sda4   * 483155968 488394751    5238784   c  W95 FAT32 (LBA)
/dev/sda5     149420628 483154867  333734240  83  Linux
/dev/sda6     125419581 137420009   12000429  83  Linux
/dev/sda7     137420073 149420564   12000492  82  Linux swap / Solaris
```


Here is the output of sudo sfdisk -d


```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=    81920, size= 20480000, Id= 7
/dev/sda2 : start= 20563200, size=104856241, Id= 7
/dev/sda3 : start=125419455, size=357735420, Id= f
/dev/sda4 : start=483155968, size=  5238784, Id= c, bootable
/dev/sda5 : start=149420628, size=333734240, Id=83
/dev/sda6 : start=125419581, size= 12000429, Id=83
/dev/sda7 : start=137420073, size= 12000492, Id=82
```


Here is the output of sudo fdisk -lu


```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98229822

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           81920    20561919    10240000    7  HPFS/NTFS
/dev/sda2        20563200   125419440    52428120+   7  HPFS/NTFS
/dev/sda3       125419455   483154874   178867710    f  W95 Ext'd (LBA)
/dev/sda4   *   483155968   488394751     2619392    c  W95 FAT32 (LBA)
/dev/sda5       149420628   483154867   166867120   83  Linux
/dev/sda6       125419581   137420009     6000214+  83  Linux
/dev/sda7       137420073   149420564     6000246   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by caljohnsmith on 2008-12-24
Your partition table looks OK now, and since you installed Mint, what is the problem? How about posting the results of the following:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your new setup.

---

### Post by N4zgu1 on 2009-01-07
Here is the result


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /BOOTMGR /ntldr /NTLDR 
                       /NTDETECT.COM /ntdetect.com /Boot /boot /BOOT

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Linux Mint 6 Felicia
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda7: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98229822

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           81920    20561919    10240000    7  HPFS/NTFS
/dev/sda2        20563200   125419440    52428120+   7  HPFS/NTFS
/dev/sda3       125419455   483154874   178867710    f  W95 Ext'd (LBA)
/dev/sda4   *   483155968   488394751     2619392    c  W95 FAT32 (LBA)
/dev/sda5       149420628   483154867   166867120   83  Linux
/dev/sda6       125419581   137420009     6000214+  83  Linux
/dev/sda7       137420073   149420564     6000246   82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: partition 4 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="AAB6D921B6D8EEB7" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda2: UUID="2C6EDB496EDB0B0A" LABEL="OS" TYPE="ntfs" 
/dev/sda4: LABEL="MEDIADIRECT" UUID="549E-00DF" TYPE="vfat" 
/dev/sda5: LABEL="Dreamlinux" UUID="a4b26e3c-3953-4385-b1ee-e5a64f01450b" TYPE="ext3" 
/dev/sda6: UUID="0a2d4546-254c-48ad-9bf4-796a63c76095" TYPE="ext3" 
/dev/sda7: UUID="e52f7348-add0-4e78-85e1-860037bf9518" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /home type ext3 (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/carlos/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=carlos)

================================== sda2/boot: ==================================

total 4024
drwxrwxrwx 1 root root    8192 2008-09-17 15:37 .
drwxrwxrwx 1 root root    8192 2008-11-19 23:22 ..
-rwxrwxrwx 1 root root   53248 2008-11-03 15:56 bcd
-rwxrwxrwx 2 root root   28672 2008-09-13 12:26 BCD.Backup.0001
-rwxrwxrwx 2 root root   32768 2008-09-17 15:30 BCD.Backup.0002
-rwxrwxrwx 2 root root   40960 2008-10-20 14:33 BCD.Backup.0003
-rwxrwxrwx 2 root root   49152 2008-11-03 08:40 BCD.Backup.0004
-rwxrwxrwx 1 root root  262144 2008-11-03 15:49 BCD.LOG
-rwxrwxrwx 2 root root       0 2006-11-15 11:41 BCD.LOG1
-rwxrwxrwx 2 root root       0 2006-11-15 11:41 BCD.LOG2
-rwxrwxrwx 1 root root    1024 2008-03-04 10:08 bootfix.bin
-rwxrwxrwx 1 root root 3170304 2008-03-04 10:08 boot.sdi
-rwxrwxrwx 1 root root   65536 2006-11-15 11:41 bootstat.dat
drwxrwxrwx 1 root root       0 2008-09-17 15:37 cs-CZ
drwxrwxrwx 1 root root       0 2008-09-17 15:37 da-DK
drwxrwxrwx 1 root root       0 2008-09-17 15:37 de-DE
drwxrwxrwx 1 root root       0 2008-09-17 15:37 el-GR
drwxrwxrwx 1 root root       0 2008-09-17 15:37 en-US
drwxrwxrwx 1 root root       0 2008-09-17 15:37 es-ES
-rwxrwxrwx 1 root root    2048 2008-03-04 16:05 etfsboot.com
drwxrwxrwx 1 root root       0 2008-09-17 15:37 fi-FI
drwxrwxrwx 1 root root    4096 2008-09-17 15:37 fonts
drwxrwxrwx 1 root root       0 2008-09-17 15:37 fr-FR
drwxrwxrwx 1 root root       0 2008-09-17 15:37 hu-HU
drwxrwxrwx 1 root root       0 2008-09-17 15:37 it-IT
drwxrwxrwx 1 root root       0 2008-09-17 15:37 ja-JP
drwxrwxrwx 1 root root       0 2008-09-17 15:37 ko-KR
-rwxrwxrwx 1 root root  386664 2006-11-02 03:51 memtest.exe
drwxrwxrwx 1 root root       0 2008-09-17 15:37 nb-NO
drwxrwxrwx 1 root root       0 2008-09-17 15:37 nl-NL
drwxrwxrwx 1 root root       0 2008-09-17 15:37 pl-PL
drwxrwxrwx 1 root root       0 2008-09-17 15:37 pt-BR
drwxrwxrwx 1 root root       0 2008-09-17 15:37 pt-PT
drwxrwxrwx 1 root root       0 2008-09-17 15:37 ru-RU
drwxrwxrwx 1 root root       0 2008-09-17 15:37 sv-SE
drwxrwxrwx 1 root root       0 2008-09-17 15:37 tr-TR
drwxrwxrwx 1 root root       0 2008-09-17 15:37 zh-CN
drwxrwxrwx 1 root root       0 2008-09-17 15:37 zh-HK
drwxrwxrwx 1 root root       0 2008-09-17 15:37 zh-TW

================================ sda4/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768


================================== sda4/Boot: ==================================

total 580
drwxr-xr-x 26 root root   4096 2008-11-04 13:59 .
drwxr-xr-x  8 root root   4096 1969-12-31 18:00 ..
-rwxr-xr-x  1 root root  16384 2008-12-23 15:00 bcd
-rwxr-xr-x  1 root root  13312 2008-12-23 15:00 bcd.log
-rwxr-xr-x  1 root root  65536 2008-11-04 14:06 BootStat.dat
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 cs-CZ
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 da-DK
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 de-DE
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 el-GR
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 en-US
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 es-ES
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 fi-FI
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 Fonts
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 fr-FR
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 hu-HU
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 it-IT
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 ja-JP
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 ko-KR
-rwxr-xr-x  1 root root 386664 2006-11-02 10:51 memtest.exe
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 nb-NO
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 nl-NL
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 pl-PL
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 pt-BR
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 pt-PT
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 ru-RU
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 sv-SE
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 tr-TR
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 zh-CN
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 zh-HK
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 zh-TW

================================== sda4/boot: ==================================

total 580
drwxr-xr-x 26 root root   4096 2008-11-04 13:59 .
drwxr-xr-x  8 root root   4096 1969-12-31 18:00 ..
-rwxr-xr-x  1 root root  16384 2008-12-23 15:00 bcd
-rwxr-xr-x  1 root root  13312 2008-12-23 15:00 bcd.log
-rwxr-xr-x  1 root root  65536 2008-11-04 14:06 BootStat.dat
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 cs-CZ
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 da-DK
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 de-DE
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 el-GR
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 en-US
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 es-ES
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 fi-FI
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 Fonts
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 fr-FR
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 hu-HU
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 it-IT
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 ja-JP
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 ko-KR
-rwxr-xr-x  1 root root 386664 2006-11-02 10:51 memtest.exe
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 nb-NO
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 nl-NL
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 pl-PL
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 pt-BR
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 pt-PT
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 ru-RU
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 sv-SE
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 tr-TR
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 zh-CN
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 zh-HK
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 zh-TW

================================== sda4/BOOT: ==================================

total 580
drwxr-xr-x 26 root root   4096 2008-11-04 13:59 .
drwxr-xr-x  8 root root   4096 1969-12-31 18:00 ..
-rwxr-xr-x  1 root root  16384 2008-12-23 15:00 bcd
-rwxr-xr-x  1 root root  13312 2008-12-23 15:00 bcd.log
-rwxr-xr-x  1 root root  65536 2008-11-04 14:06 BootStat.dat
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 cs-CZ
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 da-DK
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 de-DE
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 el-GR
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 en-US
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 es-ES
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 fi-FI
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 Fonts
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 fr-FR
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 hu-HU
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 it-IT
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 ja-JP
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 ko-KR
-rwxr-xr-x  1 root root 386664 2006-11-02 10:51 memtest.exe
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 nb-NO
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 nl-NL
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 pl-PL
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 pt-BR
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 pt-PT
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 ru-RU
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 sv-SE
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 tr-TR
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 zh-CN
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 zh-HK
drwxr-xr-x  2 root root   4096 2008-11-04 14:02 zh-TW

=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,5)
kernel		/boot/last-good-boot/vmlinuz root=/dev/sda6 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista/Longhorn (loader)
root		(hd0,3)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=0a2d4546-254c-48ad-9bf4-796a63c76095 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a4b26e3c-3953-4385-b1ee-e5a64f01450b /home           ext3    relatime        0       2
# /dev/sda7
UUID=e52f7348-add0-4e78-85e1-860037bf9518 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda6/boot: ==================================

total 25232
drwxr-xr-x  4 root root    4096 2008-12-25 14:52 .
drwxr-xr-x 20 root root    4096 2008-12-25 14:52 ..
-rw-r--r--  1 root root  507665 2008-11-04 15:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 17:46 abi-2.6.27-9-generic
lrwxrwxrwx  1 root root       1 2008-12-23 12:33 boot -> .
-rw-r--r--  1 root root   91364 2008-11-04 15:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 17:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-23 18:22 gfxmenu
drwxr-xr-x  2 root root    4096 2008-12-23 18:23 grub
-rw-r--r--  1 root root 8926464 2008-12-25 14:51 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8926287 2008-12-25 14:52 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 15:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 17:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 15:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 17:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 15:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 17:46 vmlinuz-2.6.27-9-generic

=============================== sda6/boot/grub: ===============================

total 244
drwxr-xr-x 2 root root   4096 2008-12-23 18:23 .
drwxr-xr-x 4 root root   4096 2008-12-25 14:52 ..
-rw-r--r-- 1 root root    197 2008-12-23 12:40 default
-rw-r--r-- 1 root root     15 2008-12-23 12:40 device.map
-rw-r--r-- 1 root root   9440 2008-12-23 12:40 e2fs_stage1_5
-rw-r--r-- 1 root root   9120 2008-12-23 12:40 fat_stage1_5
-rw-r--r-- 1 root root     19 2008-12-23 12:40 installed-version
-rw-r--r-- 1 root root   8224 2008-12-23 12:40 iso9660_stage1_5
-rw-r--r-- 1 root root  10144 2008-12-23 12:40 jfs_stage1_5
-rw-r--r-- 1 root root   4755 2008-12-23 18:23 menu.lst
-rw-r--r-- 1 root root   8480 2008-12-23 12:40 minix_stage1_5
-rw-r--r-- 1 root root  11296 2008-12-23 12:40 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-23 12:40 stage1
-rw-r--r-- 1 root root 125674 2008-12-23 12:40 stage2
-rw-r--r-- 1 root root  10856 2008-12-23 12:40 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sda4

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 26 18  |.X.MSDOS5.0...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 60 cc 1c  |........?....`..|
00000020  00 f0 4f 00 ed 13 00 00  00 00 00 00 02 00 00 00  |..O.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 df 00 9e 54 44  65 6c 6c 4d 44 33 70 6c  |..)...TDellMD3pl|
00000050  61 79 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |ayFAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-07
So I don't think you mentioned yet, but what exactly is the problem you are experiencing now?

---

### Post by N4zgu1 on 2009-01-08
There is no problem with linux (this time LinuxMint) but I cannot boot with Windows Vista

---

### Post by caljohnsmith on 2009-01-08
According to the menu.lst you posted, you should be able to boot Vista with the first Vista entry in the menu.lst, i.e. the one that uses (hd0,1). When you choose that entry from the Grub menu on start up, what exactly happens? Do you get any errors?

---

### Post by N4zgu1 on 2009-01-27
thanks caljohnsmith but  I reinstalled vista and now everything is working fine

---


---
title: "What is the biggest risk? Run ntfs-3g or change partition to ext3?"
date: 2007-05-08
forum: Desktop Environments
---

### Post by Azyx on 2007-05-08
I have a big disk but no possibility to back up files. I wonder which is the the biggest risk.

Run my ntfs-disk with ntfs-3g (with writingrights)or change the ntfs-partioton with gparted to ext3?

/azyx

---

### Post by taurus on 2007-05-08
Always a good idea to use ext3.  And if you need to access it from Windows, then use [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by Azyx on 2007-05-08
> **taurus said:**
> Always a good idea to use ext3.  And if you need to access it from Windows, then use [http://www.fs-driver.org](http://www.fs-driver.org).


For 1 1/2 month ago I asked about to change to ext3 from NFS becourse i don't have windows any more, but many says it's extremly risky buisness... see --> [http://ubuntuforums.org/showthread.php?t=389058](http://ubuntuforums.org/showthread.php?t=389058) 

So i don't want NTFS any more. So you say it's more risk to run with ntfs-3g than change the NTFS-partition to ext3 with lot of files (i don't want to loose the files)?

Is there anyone else with another opinion or someone with risk-figures?

/Azyx

---

### Post by taurus on 2007-05-08
You will loose all your files when you convert it from ntfs to ext3 so backup first before you do any converting.  And since you don't have Windows anymore, why even bother using ntfs filesystem!

---

### Post by Azyx on 2007-05-08
> **taurus said:**
> You will loose all your files when you convert it from ntfs to ext3 so backup first before you do any converting.  And since you don't have Windows anymore, why even bother using ntfs filesystem!


Fist. I have a lot of files but no place to backup to (movies and otherbig files). I had 2 300GB ntfs-disk there I have backed up one disk, and reformated that to ext3. but now i dont have that upportunity anymore. (No more free space to backup to)

Second. I thougt this implied that I with gparted i could change filesystem from ntfs to ext3 without loosing files

"THIS IS NOT A RECOMENDED COURSE OF ACTION

converting partition formats is extremely dangerous for most partitions (ESPECIALLY NTFS) I recomend backing up your files and the reformating instead"

Or have i misunderstod everything?

(Azyx

---

### Post by MystaMax on 2007-05-08
After reading [this FAQ]("http://www.fs-driver.org/faq.html#acc_ext3") @ fs-driver.org, it seems if I was to do this also, I'd still have all the benefits of an Ext3, is that correct?

Also, for those who have tried this and have an Ext3 partition, do you mount it as an Ext2 or Ext3? Sounds silly, but I'd like to hear some opinions and feedback. Thanks :)

---

### Post by orb9220 on 2007-05-08
[http://www.fs-driver.org/](http://www.fs-driver.org/)  is for accessing ext3 partitions  from windows. Which I use to access ext3 partitions when running xp.

The program does not answer your first question.

> Run my ntfs-disk with ntfs-3g (with writingrights)or change the ntfs-partioton with gparted to ext3?

There is no way to convert it to ext3 without losing the data or at least the possibility of losing it all. 

With that said the ntfs-3g you could mount it and start reading and writing a few test files to test if all is well. I have heard good thinks about it but also some failures.

And the reason you can't backup to DVD's or usb drive?

320GB = 73 single layer DVD's = $26 and a whole lot of time at about 4-5 disc's per hour.
or Getting another usb HD at $120-150.

Just how important is the Data to You!

---

### Post by Azyx on 2007-05-08
I know. I don't have windows anymore...

The data is not worth $100 or a lot of time. But i am a "hounter and collector person" ;) The most data that is most important I already backed up. I know there is a risk of loosing data, and I know thre also is a risk to run ntfs-3g. I have run ntfs-3g for maybe 2 month and haven't got any problems, but i haven't used it so much either.

I think I maybe could resize the ntfs-partition from 280GB to 200GB ( I have 80GB free space on the partition) Then make a new ext3 partition an shuffel over data to the new ext3 partition, and then minimize the ntfs patition again to 120, and make the ext3 partition even bigger, and so on... It just want a tip and opinions of what's the least risky way to migrate to ext3 (without bying a new disk or burning a lot of DVD.

/Azyx

> **orb9220 said:**
> [http://www.fs-driver.org/](http://www.fs-driver.org/)  is for accessing ext3 partitions  from windows. Which I use to access ext3 partitions when running xp.

The program does not answer your first question.



There is no way to convert it to ext3 without losing the data or at least the possibility of losing it all. 

With that said the ntfs-3g you could mount it and start reading and writing a few test files to test if all is well. I have heard good thinks about it but also some failures.

And the reason you can't backup to DVD's or usb drive?

320GB = 73 single layer DVD's = $26 and a whole lot of time at about 4-5 disc's per hour.
or Getting another usb HD at $120-150.

Just how important is the Data to You!

---

### Post by lotacus on 2007-05-08
That would take a long time, but it looks like it may be the only way. You could also start deleting files. As you said, you backed up the files you deemed important to you. Anything you can re-download, you can delete. It will give you something to do instead of spinning the beryl cube :)

There are also applications which you can run from a floppy or make a bootable cd/dvd from. You would have to check first to see if they support the conversion from NTFS to Ext3. The one I have always used was Partition Magic, which comes with a DOS version. You can write these using the PQmagic utility, creating a boot disk to use, or you can manually find the DOS files in the installed directory, then google on how to create a bootable cd/dvd and create it yourself, if you don't have a floppy drive.

There are similar utilities out there, you will just have to wisely google to find the correct company offering the software.

---

### Post by orb9220 on 2007-05-08
> I think I maybe could resize the ntfs-partition from 280GB to 200GB ( I have 80GB free space on the partition) Then make a new ext3 partition an shuffel over data to the new ext3 partition, and then minimize the ntfs patition again to 120, and make the ext3 partition even bigger, and so on... It just want a tip and opinions of what's the least risky way to migrate to ext3 (without bying a new disk or burning a lot of DVD.

Yes I have seen others use this approach and it seemed to work for them.

---

### Post by jimbo99 on 2007-05-08
NTFS-3G support with the NTFS Configuration Tool is more than enough to manage your NTFS partitions/file systems.  I use it in combination with XP and Linux to share data, etc.  I also use the tool under XP to read ext2 file systems--though I have problems when there is more than one EXT2/3 file system on various drives.

I just can't imagine anyone shying away from NTFS-3G.  It really does just work.

One question I have about space consumption on an EXT3 vs. NTFS file system:  Does EXT3 (which apparently is just EXT2 with journaling) have any inherent benefit in space savings in how it writes sectors/clusters to the drive?  So, could I save any notable amount of space by converting from NTFS to EXT3/2?

---

### Post by Azyx on 2007-05-10
> **orb9220 said:**
> Yes I have seen others use this approach and it seemed to work for them.

Hi.

I tried to resize and it fails. I get the advise to run with -n and -s option. I use it on an swedish ubuntu, so you may have problems to read the error-log, but here it comes.

=======================================================

GParted 0.2.5

Ändra storlek på /dev/hdc1 från 279.46 GiB till 161.53 GiB    ( ERROR )
        
kontrollera filsystemet på /dev/hdc1 efter fel och rätta (om möjligt) till dem    ( SUCCES )
        
ntfsresize -P -i -f -v /dev/hdc1
        
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/hdc1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066406912 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 172203 MB (57,4%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3251 MB 0
Multi-Record : 266536 MB 10824
$MFTMirr : 150034 MB 1
Ordinary : 300066 MB 10845
You might resize at 172202983424 bytes or 172203 MB (freeing 127864 MB).
Please make a test run using both the -n and -s options before real resizing!
ändra storlek på filsystem    ( ERROR )
        
kör simulering    ( ERROR )
        
ntfsresize -P --force --force /dev/hdc1 -s 173430439936 --no-action
        
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/hdc1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066406912 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
New volume size : 173430436352 bytes (173431 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 172203 MB (57,4%)
Collecting resizing constraints ...
Needed relocations : 19211035 (78689 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1048 > 1024), not yet supported!
Please try to free less space.
kontrollera filsystemet på /dev/hdc1 efter fel och rätta (om möjligt) till dem    ( SUCCES )
        
ntfsresize -P -i -f -v /dev/hdc1
        
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/hdc1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066406912 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 172203 MB (57,4%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3251 MB 0
Multi-Record : 266536 MB 10824
$MFTMirr : 150034 MB 1
Ordinary : 300066 MB 10845
You might resize at 172202983424 bytes or 172203 MB (freeing 127864 MB).
Please make a test run using both the -n and -s options before real resizing!
förstora filsystemet för att fylla upp partitionen    ( SUCCES )
        
kör simulering    ( SUCCES )
        
ntfsresize -P --force --force /dev/hdc1 --no-action
        
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/hdc1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066406912 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
New volume size : 300066402816 bytes (300067 MB)
Nothing to do: NTFS volume size is already OK.
förstora filsystemet för att fylla upp partitionen    ( SUCCES )
        
ntfsresize -P --force --force /dev/hdc1
        
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/hdc1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066406912 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
New volume size : 300066402816 bytes (300067 MB)
Nothing to do: NTFS volume size is already OK.
kontrollera filsystemet på /dev/hdc1 efter fel och rätta (om möjligt) till dem    ( SUCCES )
        
ntfsresize -P -i -f -v /dev/hdc1
        
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/hdc1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066406912 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 172203 MB (57,4%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3251 MB 0
Multi-Record : 266536 MB 10824
$MFTMirr : 150034 MB 1
Ordinary : 300066 MB 10845
You might resize at 172202983424 bytes or 172203 MB (freeing 127864 MB).
Please make a test run using both the -n and -s options before real resizing!

========================================

---

### Post by Azyx on 2007-05-10
[

---


---
title: "Lost  NTFS partition - need help to recover data"
date: 2009-02-01
forum: General Help
---

### Post by alexeix on 2009-02-01
Hi,

Ubuntu is my main OS, but while attempting to run a different Linux OS from a 'Live' USB stick (on my Windows PC), it somehow installed onto my NTFS hard drive, which had all my data on it.

The relevant partition no longer shows as a formatted drive - I checked it using another disk with XP on it.

So I want to try and recover the data from the hard drive and have prepared a Rescue Remix CD.  However, can I just run this and check if any files are recoverable, without actually writing anything to disk?

I say this because I don't have a Ubuntu formatted hard drive handy.

OR can I connect a USB drive to the PC to use to retrieve any files which are found?

Does that make sense?  If not, please let me know and I'll try to be more clear.
Thanks.

---

### Post by taurus on 2009-02-01
Not sure if this would help you or not but you can have a look at it.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by bumanie on 2009-02-01
Testdisk is one of the best tools to try as already suggested - it can be run from within linux or it can be downloaded form the testdisk site and run of it's own live cd. The important thing is not to write anything else over the ntfs partition that has been lost. It is often suggested that one should do a clone of the affected partition onto another drive and attempt he 'undeleting' from the cloned drive, as if it doesn't work, you can clone the original drive again and try another method of recovery. 
There is also ntfsprogs in ubuntu and the ntfsundelete function. To use ntfsundelete, you do need another hard drive to save the information to. It must be of at least equal size to the partition you are trying to recover.
I would try testdisk first, then ntfsundelete if testdisk doesn't work. If you can't retrieve the entire filesystem, you should be able to retrieve individual files via photorec, which, despite it's names can recover in excess of 100 file types.
Photorec is part of the testdisk program. Hope this makes sense to you. Go to link already posted, there are some tutorials on the site.

---

### Post by Gizenshya on 2009-02-01
I was just about to post a similar topic...

on mine, a ~30 GB partition (also ntfs) was lost.  I think the partition table got corrupted.  So, thee is no file table or anything (are they recoverable?), so I think I would need to scan the entire 'empty space' where it used to be for files and recover them.

does testdisk do this?

edit:  also, you mentioned doing a byte-for-byte backup of it first.

how would I go about doing such a backup (for unused space)?  what program(s) would I need?  would I need to be able to mount whatever file it is as a virtual drive to get it to work?  or would I need another physical drive to extract it to to do the tests?

I have drives.  I'd rather just mount it as a file, though, as it would take quite a while to transfer 30 GB back and forth to drives a few times before even starting:(

and disk space isn't an issue.

---

### Post by alexeix on 2009-02-01
Thanks for the responses.

So to clarify, in Windows Disk Management, the partition shows as 'unallocated space'.

I've read the tutorials, but am still not clear about whether or not I can just do a test run from a Live CD to check if the data is still available.

I don't have another hard drive available immediately and of course, I don't want to write any data to the problem drive.

Can I run Testdisk and create a log file, without writing it?

The affected drive is 500GB, but probably has around 300GB of data on it.

---

### Post by caljohnsmith on 2009-02-01
**Gizenshya**, yes testdisk can help you recover lost/deleted partitions, and I would strongly recommend using only the "deep search" results in order have the best chance of recovering the correct partition. If you want to try testdisk from Ubuntu, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
Check to see that you are using testdisk 6.9 or later, because 6.9 has much better support for NTFS partitions. I can give you an alternate method to download the latest testdisk if you need it. So after starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results if you would like help recovering your partition. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing. We can work from there if you want.

---

### Post by caljohnsmith on 2009-02-01
**Alexeix**, how about running testdisk from your Live CD, and that way you won't have to worry about writing to the HDD in question. But first, how about opening a terminal (Applications > Accessories > Terminal) while you are on the Live CD, and please post:
```
sudo fdisk -lu
```
That will give us some basic info about what partitions currently exist on that HDD.

---

### Post by Gizenshya on 2009-02-01
thanks :)

also, you mentioned doing a byte-for-byte backup of it first.

how would I go about doing such a backup (for unused space)? what program(s) would I need? would I need to be able to mount whatever file it is as a virtual drive to get it to work? or would I need another physical drive to extract it to to do the tests?

I have drives. I'd rather just mount it as a file, though, as it would take quite a while to transfer 30 GB back and forth to drives a few times before even starting

and disk space isn't an issue.

ohh.. and I'm currently downloading/installing 8.10 (from 8.04), so its going to be at least 5 hours before I can start :(

---

### Post by caljohnsmith on 2009-02-01
**Gizenshya**, you can make a byte-for-byte copy of the partition by doing:
```
sudo dd if=/dev/[COLOR="Blue"]sdXY[/COLOR] of=[COLOR="Blue"]sdXY[/COLOR]_image bs=10M conv=notrunc
```
And replace sdXY with the partition in question. When you run that command, it will create the "sdXY_image" file in the directory where you run the command; you could either give an absolute path to where you want to save the partition image file, or you could navigate into the directory where you want to save the partition image and run the command above there. You will probably want to mount a partition from some other drive that is large enough to hold the sdXY_image file and save the image file there. Once you have the partition image file created, if I remember correctly you can run testdisk on it directly without even mounting it:
```
sudo testdisk sdXY_image
```
Or if that doesn't work, you can always mount the sdXY_image file as a loop device, and I can help you with that if necessary. If you use testdisk directly with the partition image, it shouldn't be necessary to do a deep search. See what options testdisk gives you for that partition when you run it. Let us know how it goes.

---

### Post by Gizenshya on 2009-02-01
ok...

but the partition table shows up as unallocated space (or whatever).  Its a 100gb drive, with 3 approximately equal partitions.  The other 2 were fine, and I've recovered all the data from them.

So that leaves the 2 partitions, and a bunch of unallocated space.  But with the unallocated space, correct me if I'm wrong, I thought there wouldn't be an SDxy (location).  Instead of doing /sda1 for example, would it be possible to do something along the lines of (logically) 1-(the other 2 partitions)?

or would I have to create an image of the entire 100gb drive to do a backup? :(

---

### Post by caljohnsmith on 2009-02-01
Gizenshya, sorry I misunderstood you; you shouldn't need to make an image of the entire HDD, you could make an image file of just the unallocated space, and then use testdisk to try and recover the partition. Once you get Ubuntu running, how about first posting:
```
sudo fdisk -lu
```
And then we will be able to see where the unallocated space is, and I can give you specific directions for making an image file of it if you like.

---

### Post by alexeix on 2009-02-01
> **caljohnsmith said:**
> **Alexeix**, how about running testdisk from your Live CD, and that way you won't have to worry about writing to the HDD in question. But first, how about opening a terminal (Applications > Accessories > Terminal) while you are on the Live CD, and please post:
```
sudo fdisk -lu
```
That will give us some basic info about what partitions currently exist on that HDD.

Here you go (this is the installation of Webconverger which was somehow installed on my NTFS drive)>>>

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
87 heads, 56 sectors/track, 200487 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000774f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      487423      243711+  83  Linux

---

### Post by caljohnsmith on 2009-02-01
That's a good sign, alexeix, because the only partition on that HDD is the 200 MB linux partition; most likely your NTFS partition data is mostly intact, but it may be hard to get to it. How about running the testdisk procedure from post #6 to see if testdisk can find the lost NTFS partition. Let me know how that goes or if you run into problems.

---

### Post by alexeix on 2009-02-01
Good to hear. :)

Will Testdisk take a long time to run?

If so, I'll leave it overnight, but I just wanted to check.

---

### Post by caljohnsmith on 2009-02-01
It definitely won't take overnight to run the testdisk "deep search" even on your 500 GB HDD; I'm guessing it might take 20 minutes or so is all (or at least in that ballpark, but not hours). How about giving it a shot and let me know the results.

---

### Post by Gizenshya on 2009-02-01
question...

would it be possible to mount the drive as read only and then run testdisk?

would this essentially have the same effect as running backing it up (in terms of not tampering with the data?

another thing...

in vista, when I was backing up the other partitions,I was getting weird errors.

for every file I cut and pasted, I would get something like an I/O error for deleting the empty files. I had to click ok, then delete them, and then refresh to see them gone.

so.. the hard drive may be on the fritz as well.  would it be better to back it up first anyway similar to the way you mentioned earlier, even if its ro?

---

### Post by alexeix on 2009-02-01
> **caljohnsmith said:**
> It definitely won't take overnight to run the testdisk "deep search" even on your 500 GB HDD; I'm guessing it might take 20 minutes or so is all (or at least in that ballpark, but not hours). How about giving it a shot and let me know the results.

Sorry, but when running Ubuntu from a live disk, how do I install and run Testdisk?

It doesn't appear in Synaptic Package Manager.

---

### Post by caljohnsmith on 2009-02-01
**Gizenshya**, I don't know of any way to mount the drive as read-only, but as long as you are careful with testdisk, testdisk will not write to that drive unless you tell it to do so like when you are writing a new partition table. If the HDD is going bad though, I would use something like dd_rescue to try and make an image of that entire HDD to some other HDD. You can install and run dd_rescue with:
```
sudo apt-get install ddrescue
sudo dd_rescue -b 10M /dev/[COLOR="Blue"]sda[/COLOR] HDD_image
```
And change sda to be whichever is the drive in question. 

**Alexeix**, did you first enable the Universe repository as given in the directions in post #6? If so, running the "apt-get" command in that post should install testdisk, you don't have to use Synaptic.

---

### Post by alexeix on 2009-02-01
> **caljohnsmith said:**
> 

**Alexeix**, did you first enable the Universe repository as given in the directions in post #6? If so, running the "apt-get" command in that post should install testdisk, you don't have to use Synaptic.

Hmmm...have run Testdisk, but all I got in the log file was this (see below).  I didn't have an option to run a deep scan, buyt the analysis I did took around an hour.
it looks like maybe I didn't run it correctly.
I know the Superbowl is about to start, so I suppose I may not get a reply until later/tomorrow...

;-)

Sun Feb  1 22:13:23 2009
Command line: TestDisk

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
Linux version (ext2fs lib: 1.41.3, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none)
Hard disk list
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA Hitachi HDT72505

Disk /dev/sda - 500 GB / 465 GiB - ATA Hitachi HDT72505
Partition table type: Intel

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Geometry from i386 MBR: head=87 sector=56
check_part_i386 failed for partition type 83
Current partition structure:
No EXT2, JFS, Reiser, cramfs or XFS marker
 1 * Linux                    0   0  2    30  86 56     487423
 1 * Linux                    0   0  2    30  86 56     487423

---

### Post by alexeix on 2009-02-01
So in Testdisk, this is what I did:

Create > Selected disk > Intel > Analyse > Quick Search.

---

### Post by alexeix on 2009-02-02
Any feedback on how I can do a more detailed analysis?

Thanks in advance!

---

### Post by Gizenshya on 2009-02-02
> **caljohnsmith said:**
> Gizenshya, sorry I misunderstood you; you shouldn't need to make an image of the entire HDD, you could make an image file of just the unallocated space, and then use testdisk to try and recover the partition. Once you get Ubuntu running, how about first posting:
```
sudo fdisk -lu
```
And then we will be able to see where the unallocated space is, and I can give you specific directions for making an image file of it if you like.

ok, hooked it up and apparently its the first time I've tried it in ubuntu, as I got an error I don't remember.

but first, the output from sudo fdisk -lu

```
Disk /dev/sdd: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11d4116c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63    66958919    33479428+   7  HPFS/NTFS
/dev/sdd2        66958920   195366464    64203772+   f  W95 Ext'd (LBA)
/dev/sdd5        66958983   133869644    33455331    b  W95 FAT32
/dev/sdd6       133869708   195366464    30748378+   b  W95 FAT32

```

thats for the drive in question.

Two of the partitions are still working and mount fine.  but the one refuses to mount (I can't make sense of the above code...).  but here is the error message and the output from the extra info tab thingy.

"**Cannot mount volume**
Unable to mount volume.

_D_etails
$MFTMirr does not match $MFT (record 1). Failed to mount '/dev/sdd1': input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/fakeRAID hardware. In the first case run chkdsk /f on windows then reboot into Windows TWICE. The usage of the /f parameter is very important! If you have SoftRAID/fakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for the details."

so what should I do?

:'(

---

### Post by caljohnsmith on 2009-02-02
Gizenshya, I don't understand why you say your NTFS partition is lost and now unallocated space, because fdisk shows your NTFS partition. Also, there is no unallocated space on your 100 GB drive according to the fdisk output. It looks like the partition you are talking about is sdd1, the only NTFS partition on that drive. How about doing the following to make an image of that partition:
```
sudo apt-get install ddrescue
sudo dd_rescue -b 10M /dev/sdd1 sdd1_image
```
That will create the sdd1_image file in whichever directory you run the dd_rescue command in. sdd1 is about 33 GB, so make sure you have room for it. Once the copying is done, how about doing:
```
sudo testdisk sdd1_image
```
Select "Proceed", "None" (Non-partitioned media), "Advanced", "Boot", and finally "Rebuild BS". When it gives you a warning about boot sectors not matching or not being identical, select "write". Then quit testdisk and do:
```
sudo mkdir sdd1_dir
sudo mount -t ntfs-3g -o loop sdd1_image sdd1_dir && ls -l sdd1_dir
```
And please post the output. We can work from there.

---

### Post by Gizenshya on 2009-02-02
well, windows told me that was the case, and said it needed to be formatted.  I knew it didn't need to be formatted...but I thought it had it right that there was no partition anymore.  guess I was wrong.  but hey, that seems like a good thing :)

well... I ran the code you gave, but on the backup code I did it a little different. instead of sdd1_image, I put /host/100GBIMAGE/sdd1_image (because thats a partition where there is plenty of space).

it was going well for about 3 gb, then I started getting errors.

I'll post them all if you like, but here are the last two and a message at the bottom (just to be concise)

```
dd_rescue: (info): ipos:   3082575.5k, opos:   3082575.5k, xferd:   3082575.5k
                *  errs:     31, errxfer:        15.5k, succxfer:   3082560.0k
             +curr.rate:    31250kB/s, avg.rate:     8818kB/s, avg.load:  2.9%
dd_rescue: (warning): /dev/sdd1 (3082575.5k): Input/output error!

dd_rescue: (info): ipos:   3082576.0k, opos:   3082576.0k, xferd:   3082576.0k
                *  errs:     32, errxfer:        16.0k, succxfer:   3082560.0k
             +curr.rate:        0kB/s, avg.rate:     5806kB/s, avg.load:  1.9%
dd_rescue: (warning): /dev/sdd1 (3082576.0k): Input/output error!



Bad block: 6165152


```

its already put out another error.  every time, the errs: count goes up by 1, and the errxfer: count goes up by 5k.

ohh, and it reports another bad block... (now showing 6165153).

just wait and hope it passes or what?

btw, I REALLY appreciate your help with this! :D

---

### Post by caljohnsmith on 2009-02-02
Unfortunately, there's not much you can do but let dd_rescue keep chugging along and skipping whatever bad sectors it finds. How bad do you want the data on the sdd1 partition? It's clear with all those errors it's going to be tough to recover files from that partition, and of course some files won't be recoverable because of the bad sectors. So if you want to recover anything on that partition, I think you will need to be prepared to put a significant amount of time and effort into it. Maybe you'll get lucky and it won't be too difficult to recover most of the files, but it would be good to be prepared for the worst.

---

### Post by Gizenshya on 2009-02-02
well, I'll probably be spending a lot of time the next couple days in computer labs around campus anyway (lots of tests starting tomorrow), so it can just sit and do its thing.  Going half a kb per minute for a 30gb drive would take quite a while, though... but I think most of it will be there.

I was having errors (it was frm an older computer, and I thought it was the RAM).  the errors became more common.. then I started having boot problems.  then it wouldn't fully boot.  then nothing.  so I stuck in an external case and backed up stuff from the other 2 partitions (got almost all the data off of them fine, very little if any lost).  I suspect it will be similar with this partition...

but that was my main partition for a long time.  Ironically, I had a new drive on the way as I was about to upgrade when it crashed.  So, I didn't have a chance to backup the drive, which has lots of pictures on it.  About 10GB or so of it is programs (xp, and games mostly), the rest is files I don't have backed up :(

its definitely worth it, though.


atm...

Bad block: 6165191
and errs: 71

edit: I just noticed, in between a couple of the last few bad sectors it seems to have transferred a few MB between errors.  hopefully its fairly isolated in just a couple spots...

so, I'm off to a computer lab for a few hours to work on some other stuff while it works :)

---

### Post by Gizenshya on 2009-02-02
ok,there were a few more errors right in a row, and then it was all clear after that.  So only a span of about 5 mb of sectors had bad patches.

```
Summary for /dev/sdd1 -> /host/100GBIMAGE/sdd1_image:
dd_rescue: (info): ipos:  33479428.0k, opos:  33479428.0k, xferd:  33479428.0k
                   errs:     80, errxfer:        40.0k, succxfer:  33479388.0k
             +curr.rate:    96603kB/s, avg.rate:     2763kB/s, avg.load:  1.0%

```

I now have a 31.9 gb image file :)

I'll edit in a minute and do what you mentioned earlier to the image.

---

### Post by Antioch on 2009-02-03
I followed these instructions, having similarly messed up the partition table information of one of my disks. I was able to recreate the partition table for the partition in question using the TestDisk utility and recover 100% of my files (as I the raw data wasn't changed, only the partition table map). The utility didn't perfectly restore the entire disk structure, so I will do a reformat after I back up the data.

I just wanted to report on my success and say thanks as a thread lurker ;)

---

### Post by alexeix on 2009-02-03
> **alexeix said:**
> 
Sun Feb  1 22:13:23 2009
Command line: TestDisk

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
Linux version (ext2fs lib: 1.41.3, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none)
Hard disk list
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA Hitachi HDT72505

Disk /dev/sda - 500 GB / 465 GiB - ATA Hitachi HDT72505
Partition table type: Intel

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Geometry from i386 MBR: head=87 sector=56
check_part_i386 failed for partition type 83
Current partition structure:
No EXT2, JFS, Reiser, cramfs or XFS marker
 1 * Linux                    0   0  2    30  86 56     487423
 1 * Linux                    0   0  2    30  86 56     487423

Do you have any suggestions based on the results of the analysis I ran?

I'm stuck at the moment.

:(

---

### Post by caljohnsmith on 2009-02-03
> **alexeix said:**
> Do you have any suggestions based on the results of the analysis I ran?

I'm stuck at the moment.

:(
I don't know how to help you, because I asked you to run the testdisk "deep search" procedure in post #6; yet in your reply in post #20, you said you only ran the "quick search". Unless you run the deep search, I can't help you, because the quick search results are unreliable.

---

### Post by Antioch on 2009-02-03
CalJohnSmith, don't mean to thread hijack but I feel like it's better to ask in this thread as it is more relative.

I used TestDisk to recover an NTFS partition (sda5 I think it's called in the fdisk printouts from my other thread). When I selected the partition to recover, it worked fine. However, TestDisk created an extended partition in which it placed the NTFS as a logical partition. Is there any way to convert the extended+logical partition into a primary partition - or do I have to copy all data and reformat?

Thanks for your help, as always.

---

### Post by caljohnsmith on 2009-02-03
Sure Antioch, it's possible to convert a logical partition into a primary partition. And just for future reference, it's probably worth mentioning that when you recover the partition in testdisk, you can often choose between "P" for primary or "L" for logical; it depends on what other partitions you are also trying to recover whether you have the choice or not. But just out of curiosity, why do you want that NTFS partition to be primary? Even if it has Windows on it, you can boot Windows from a logical partition with Grub for example; if you definitely want that partition to be a primary partition, that's fine though. But changing a logical partition to a primary partition is a little bit off-topic for this partition recovery thread, so how about starting a new thread and please post:
```
sudo fdisk -lu
```
PM me with the link to your new thread, and we can work from there. :)

---

### Post by alexeix on 2009-02-03
> **caljohnsmith said:**
> I don't know how to help you, because I asked you to run the testdisk "deep search" procedure in post #6; yet in your reply in post #20, you said you only ran the "quick search". Unless you run the deep search, I can't help you, because the quick search results are unreliable.

Hi,

I couldn't find the 'deep search' option, but have now.  
I'm running it as I type and will post back with the results.

Not sure how I'll get them onto this post though, as my Ubuntu Live disc kept failing and I had to use Ubuntu Rescue Remix.

I'll work something out.
Cheers.

---

### Post by alexeix on 2009-02-03
Results of the deep analysis...

PARTITION            START           END            SIZE IN SECTORS

D FAT16 > 32M     0   0   2      30   86  55       487422  [DEBIAN_LIVE]
D HPFS - NTFS     0  32  33     60801 47  46       976769024 [DATAPART1]

If I highlight the first line, I get:

FAT16, 249 MB/237 MiB

If I highlight the second line, I get:

NTFS found using backup sector!,500 GB/465 GiB

Am I wrong in thinking that my data may be fully intact?

What do I have to do now?
Thanks for your help and patience!
:)

---

### Post by caljohnsmith on 2009-02-03
OK, that looks at least somewhat promising alexeix. Make sure to keep that first partition marked as "D", but select the DATAPART1 partition, and using your right/left arrow keys, mark it as "P". Then press enter to continue, and then in the next screen select to write the new partition table. After that, quit testdisk and please post the output of:
```
sudo fdisk -lu
```
And that should show your new partition, probably "sda1". Use that and try:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
If you get a mount error, let me know exactly what it is and we can go from there.

---

### Post by alexeix on 2009-02-03
Before reading your last reply, I highlighted the second line and pressed 'P' to list files.
According to the results, it seems that that data may be there, at least the file names and quantity suggest so.

So onto your suggestion, I marked DATAPART1 as 'P', press <enter> to continue and then wrote the new partition.

At this point, I get the following screen for the relevant partition:

Boot sector
Status: Bad

Backup boot sector
Status: OK

Sectors are not identical

A valid NTFS boot sector must be present in order to access any data; even if the partition is not bootable.

<Quit>  <List>  <BackupBS>  <RebuildBS>  <Dump>

Which option should I select?  Should I go with your original suggestion to run <sudo fdisk -lu>?

It's 00:55 here in  the UK, so I won't be up much longer - therefore may select the <Quit> option.

---

### Post by alexeix on 2009-02-03
Will be up for another 10 minutes or so.

:)

---

### Post by caljohnsmith on 2009-02-03
Choose the "Rebuild BS" option first, do whatever it says after that (I think it is "write"), and if you have the option after that to go back and do "Backup BS", use that option too. Let me know how it goes.

---

### Post by alexeix on 2009-02-03
Looks good...I've reconnected my XP drive and when I boot up, I can now see the datapart1 partition and its contents.

Strangely, when I try to view any of my movie files, there's no audio, but the video is perfect.

I think it might be a problem with the audio on the PC, but I'll look into it tomorrow.

Thanks a lot for your help and I'll post back to confirm it's fixed!

---

### Post by alexeix on 2009-02-03
Audio is fine.

Thanks a lot for your assistance; this has saved me a lot of grief!

:D

---

### Post by caljohnsmith on 2009-02-04
Congratulations on your successful recovery of your NTFS partition, alexeix; glad to hear most of your files seem to be intact and OK. :)

---


---
title: "Can't access dead hard drive"
date: 2005-12-20
forum: Desktop Environments
---

### Post by awtomlinson on 2005-12-20
I have a reiserfs /home partition.  Something with the xorg server crashed and ruined my /home partition, i lost some data, but nothing important.  i have since reinstalled breezy.  i can still access my old /home partition, but it is extremely slow, the pc will pause or freeze for minutes while accessing this partition.  the problem is, while the files are there, i can't copy the files from this damaged partition to another drive because of this slow/halted access.  the copying files dialogue will appear, but nothing ever happens.  the dialogue just hangs there for a few minutes and then disappears.  how can i transfer my valuable info from this nearly dead partition?

---

### Post by awtomlinson on 2005-12-20
again, i can access and open most of the files on this nearly dead partition, so i know that they are still there.

---

### Post by Gandalf on 2005-12-20
have you tried to force check on it?

man fsck for more information

---

### Post by awtomlinson on 2005-12-20
i haven't tried this gandalf.  i'm not very good from the terminal.  can you help?  the partition in question is /dev/hda4.  would i do fsck /dev/hda4.  i just want to make sure that i don't delete anything.  what exactly would this do?

---

### Post by Gandalf on 2005-12-20
try 
sudo fsck.reiserfs /dev/hda4

these are the Exit code:
```

EXIT CODES
       reiserfsck uses the following exit codes:
          0 - No errors.
          1 - File system errors corrected.
          2 - Reboot is needed.
          4 - File system fatal errors left uncorrected,
              reiserfsck --rebuild-tree needs to be launched.
          6 - File system fixable errors left uncorrected,
              reiserfsck --fix-fixable needs to be launched.
          8 - Operational error.
          16 - Usage or syntax error.

```

you may want to read man fsck.reiserfs first, but it's safe to do fsck.reiserfs /dev/hda4

---

### Post by awtomlinson on 2005-12-20
well, since trying to move the files to my external drive, this /home partition is now inaccessible.  it shows as unknown type in gparted.  gparted also says that the filesystem is damaged.  someone please help!  all of my valuable info (around 100gb) is there.

---

### Post by awtomlinson on 2005-12-20
receive the following message when running fsck:

reiserfs_open: the reiserfs superblock cannot be found on /dev/hda4.
Failed to open the filesystem.

If the partition table has not been changed, and the partition is
valid  and  it really  contains  a reiserfs  partition,  then the
superblock  is corrupted and you need to run this utility with
--rebuild-sb.

will the --rebuild-sb command kill all hopes of recovering the data?

---

### Post by Gandalf on 2005-12-20
sorry am not sure about if the files would still be available or not, anyone else did already that?

---

### Post by awtomlinson on 2005-12-20
my fdisk listing looks correct for /dev/hda4 as far as start, end, and blocks go.  but now, instead of reiserfs, the type now displays as simply linux.

---

### Post by three_sixteen on 2005-12-20
I dont know how you have the drive formatted..

[http://www.runtime.org/downloads.htm](http://www.runtime.org/downloads.htm)

---

### Post by awtomlinson on 2005-12-20
originally, it was formatted as reiserfs, but now, its not showing as simply linux.

---

### Post by Gandalf on 2005-12-20
that's because the super block is lost, ur only hope is to try to rebuilt it as mentioned by the results above

---

### Post by awtomlinson on 2005-12-20
i understand gandalf, but what can i do to try to preserve the data before doing the rebuild?

---

### Post by Gandalf on 2005-12-20
reading the man page
> 
--rebuild-sb
    This option recovers the superblock on a Reiserfs partition. Normally you only need this option if mount reports "read_super_block: can't find a reiserfs file system" and you are sure that a Reiserfs file system is there. But remember that if you have used some partition editor program and now you cannot find a filesystem, probably something has gone wrong while repartitioning and the start of the partition has been changed. If so, instead of rebuilding the super block on a wrong place you should find the correct start of the partition first.


i don't think it will delete data, instead it will preserve them, but please try for example to go an irc channel to ask for fast answer about wether it preserve them or not, i cannot confirm as i haven't tried it

---

### Post by awtomlinson on 2005-12-21
well, i used dd to copy the ruined partition to an .img file on my external hard drive.  i got no errors, but no .img file was created, just a bunch of files and folders were on my external drive.  most of these files and folders are of unknown file types, and most have japanese/chinese lettering and some have what looks like russian or cyrillic lettering.  i didn't see anything normal, no data from when the partition was functioning properly.  additionally, these files and folders totalled only a couple of gigs, whereas the original partition was nearly 200gb.  do i have any chance of recovering the data by rebuilding the superblock and file system tree with fsck?  additionally, it looks like this ruined partition starts and stops and the correct blocks, so i wouldn't have to find the true starting point of the partition when i rebuild the superblock.

---

### Post by awtomlinson on 2005-12-21
someone please help

---

### Post by awtomlinson on 2005-12-21
please

---

### Post by awtomlinson on 2005-12-21
tried to rebuild the file structure and received the following error:

The problem has occurred looks like a hardware problem. If you have
bad blocks, we advise you to get a new hard drive, because once you
get one bad block  that the disk  drive internals  cannot hide from
your sight,the chances of getting more are generally said to become
much higher  (precise statistics are unknown to us), and  this disk
drive is probably not expensive enough  for you to you to risk your
time and  data on it.  If you don't want to follow that follow that
advice then  if you have just a few bad blocks,  try writing to the
bad blocks  and see if the drive remaps  the bad blocks (that means
it takes a block  it has  in reserve  and allocates  it for use for
of that block number).  If it cannot remap the block,  use badblock
option (-B) with  reiserfs utils to handle this block correctly.

bread: Cannot read the block (6935674): (Input/output error).

Aborted

do i have any hope?  detailed instructions will be much appreciated, i am not familiar with fsck

---

### Post by cwaldbieser on 2005-12-21
[QUOTE=awtomlinson]tried to rebuild the file structure and received the following error:

The problem has occurred looks like a hardware problem. If you have
bad blocks, we advise you to get a new hard drive, because once you
get one bad block  that the disk  drive internals  cannot hide from
your sight,the chances of getting more are generally said to become
much higher  (precise statistics are unknown to us), and  this disk
drive is probably not expensive enough  for you to you to risk your
time and  data on it.  If you don't want to follow that follow that
advice then  if you have just a few bad blocks,  try writing to the
bad blocks  and see if the drive remaps  the bad blocks (that means
it takes a block  it has  in reserve  and allocates  it for use for
of that block number).  If it cannot remap the block,  use badblock
option (-B) with  reiserfs utils to handle this block correctly.

bread: Cannot read the block (6935674): (Input/output error).

Aborted

do i have any hope?  detailed instructions will be much appreciated, i am not familiar with fsck[/QUOTE]

Since you have another hard disk to work with, maybe you should try using GNU parted to copy your messed up partition and try running fsck on that.  You can experiment on the copy, and if you mess something up, you could just copy it and try something else.

---

### Post by awtomlinson on 2005-12-21
cbaldwieser, thanks.  i wouldn't know how to do this.  can you help, with detailed instructions?  also, i installed qtparted, and it can see this partition as reiser, with the correct size.

---

### Post by poptones on 2005-12-21
Man I'm sorry I missed yur earlier posts. 

Ideally you have two copies. You should have one of your bad partition on a good partition, and you should have a copy of that one to work on so you don't bork your only good copy if you make a mistake.

How is your external drive formatted? And how large is it?

---

### Post by awtomlinson on 2005-12-21
i used dd to copy the ruined partition to an .img file on my 300 gb external fat2 hard drive. i got no errors, but no .img file was created, just a bunch of files and folders were on my external drive. most of these files and folders are of unknown file types, and most have japanese/chinese lettering and some have what looks like russian or cyrillic lettering. i didn't see anything normal, no data from when the partition was functioning properly. additionally, these files and folders totalled only a couple of gigs, whereas the original partition was nearly 200gb

---

### Post by awtomlinson on 2005-12-21
i take the part back about qtparted properly seeing the partition, everything is correct except for the used size.  here is the complete setup for the 250gb drive:

hda1-windows ntfs-34.18gb total size, 24.62 gb used, starts at 0.03, ends at 34.18
hda2-linux swap-478.50mb total size, o used, starts at 34.18, ends at 34.65
hda3-reiser-18.63gb total size, 6.58gb used, starts at 34.65, ends at 53.28
hda4-reiser-180.48gb total size, 2 tb used, starts at 53.28, ends at 233.76

so, everything is correct except for the used size of hda4, which is listed at 2 tb, even though the total size is only 180.48gb.  

here is what fdisk -l shows:

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/hda2            4463        4523      489982+  82  Linux swap / Solaris
/dev/hda3            4524        6955    19535040   83  Linux
/dev/hda4            6956       30515   189245700   83  Linux

---

### Post by awtomlinson on 2005-12-21
poptones, i meant to say earlier that my external hard drive was 300gb formatted as fat32

---

### Post by poptones on 2005-12-21
I don't believe you are going to have much luck copying a 200gb image to fat32. 

Do you have another drive you can partition? Ideally you will create another partition the same block size as the one you have and just dd it over. 

But do I understand correctly that you already tried a recovery on the bad partition? If it was trying to *rebuild* something (as opposed to just checking it) that means it was writing to the partition - which means the partition would be more borked now than it was when you started... not good. 

For future reference you should never run a recovery operation on data you can't afford to lose, and you shouldn't run a recover on the bad disc because the bad disc *is bad* and the process will inevitably fail, possibly further corrupting the data tables in the process.

---

### Post by awtomlinson on 2005-12-22
poptones, so am i basically out of luck?  i only really need to recover about 60gb of mp3 files.  can you suggest anything else?  i know folks like the fbi can recover anything from a hard drive, no matter the condition of it almost.  surely, there is something similar available commercially.

---

### Post by awtomlinson on 2005-12-22
what file format should i use to accomplish this poptones?  i don't really trust reiser anymore.

---

### Post by dto on 2005-12-22
[QUOTE=awtomlinson]i know folks like the fbi can recover anything from a hard drive, no matter the condition of it almost.  surely, there is something similar available commercially.[/QUOTE]
Unfortunately, whenever I've heard of someone needing or recommending a commercial data recovery service for a damaged hard drive, it is inevitably accompanied by the term "thousands of dollars".  :(

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-22
The problem you are having isn't due to reiserfs, it's due to a bad hard drive. No filesystem (except for one on a raid) is going to live through that sort of failure.  I have had much better experiences with these sorts of failures using reiser than with ext3 and I would suggest you continue using it. You'll probably be able to recover a good bit of that data but the number one priority is getting it copied off the failing drive before you lose any more clusters. Certain failures can cause you to lose more and more data every minute the drive is running under power, so it's important you do this ASAP.

If you don't mind repartitioning the external drive then run whatever tool you are comfortable with and make a partition on that drive 23559 blocks in size (exactly the same size as the one you have). Then copy the entire partition to it using dd.

Example: if your external drive is mounted as sda, and the partition you make is partition 1...

dd bs=4096k if=/dev/hda4 of=/dev/sda1

Let it run til it reports its finished, then run fsck.reiserfs on that partition. It will tell you what steps to follow (ie if it tries to build the superblock and detects more errors it may tell you to rerun the fsck using --rebuild-tree). If it has to do this it will likely take a pretty long time (possibly several hours). When it's done all your files may be in lost&found, but if things aren't too bad on the failing drive you will probably recover most of your data.

---

### Post by briancurtin on 2005-12-22
[QUOTE=awtomlinson]i know folks like the fbi can recover anything from a hard drive, no matter the condition of it almost.  surely, there is something similar available commercially.[/QUOTE]
my dad looked into this about a week ago after his hard drive died and he didnt have anything backed up becuase he really didnt have anything important, until he realized some stuff he was working on a while ago. i dont want to misquote numbers, but the price was far, far, far too much to even consider. hes just redoing it in python, and it is claimed to not really be that big of a deal compared to the large quoted price haha.

60 gbs of mp3s cost you nothing. if you lose them, sorry, but all they really cost you in the first place were a bunch of mouse clicks.

---

### Post by awtomlinson on 2005-12-22
i'm wondering if the hard drive itself is bad, or if something corrupted it.  strange as it sounds, i believe that xorg corrupted my /home partition.  it could be coincidental, but this started happening just after an xorg crash.  see the following long thread:  

[http://ubuntuforums.org/showthread.php?t=86972&highlight=blank+screen+death](http://ubuntuforums.org/showthread.php?t=86972&highlight=blank+screen+death)

the rest of the hard drive (ntfs, swap, & / reiser partitions) are fine at this point.  i did a badblock test, and there are many.  is a bad block correctable (ie by formatting), or does the drive need to be replaced?

---

### Post by awtomlinson on 2005-12-22
also, do i have to make a partition on the external drive that is 23559 blocks in size (exactly the same size as the corrupted one)?  the reason i ask is that i seem to have bought one of those borked externals that won't allow you to create partitions on it.  only one partition is possible.

---

### Post by cwaldbieser on 2005-12-22
[QUOTE=awtomlinson]also, do i have to make a partition on the external drive that is 23559 blocks in size (exactly the same size as the corrupted one)?  the reason i ask is that i seem to have bought one of those borked externals that won't allow you to create partitions on it.  only one partition is possible.[/QUOTE]
I would hazard to guess that if the partition is larger than the one you are copying from, it still might work.

---

### Post by cwaldbieser on 2005-12-22
[QUOTE=awtomlinson]i'm wondering if the hard drive itself is bad, or if something corrupted it.  strange as it sounds, i believe that xorg corrupted my /home partition.  it could be coincidental, but this started happening just after an xorg crash.  see the following long thread:  

[http://ubuntuforums.org/showthread.php?t=86972&highlight=blank+screen+death](http://ubuntuforums.org/showthread.php?t=86972&highlight=blank+screen+death)

the rest of the hard drive (ntfs, swap, & / reiser partitions) are fine at this point.  i did a badblock test, and there are many.  is a bad block correctable (ie by formatting), or does the drive need to be replaced?[/QUOTE]

A bad block basically means that the media (the magnetic platter) has worn out on that area of the disk, and writing to it will no longer work.  Sometimes, you just get one or two of these, and your filesystem just makes a note not to try to use that part of the disk anymore.  When you start getting a lot of them, it generally means it is time to get a new drive.

All drives tend to fail after some time, so it is a good strategy to make regular backups of important files (resumes, pictures, spreadsheets, thesis, or whatever).

It is really unlikely that an Xorg crash could cause any kind of permanent damage to your drive.  

I would suggest that you might want to back up any important data on the working partitions (the NTFS partition, for example) as well, and then replace the drive as soon as possible.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-22
Yes, more than likely the bad drive caused the crash. Xorg is not going to cause a bunch of bad blocks on your drive.

If you cannot repartition it, reformat it using reiserfs, mount it, then back up your failing drive via 

dd bs=4096k if=/dev/hda4 of=/dev/sda1/drive.img

Once you have that the image can be mounted via loopback and fsck'd.

---


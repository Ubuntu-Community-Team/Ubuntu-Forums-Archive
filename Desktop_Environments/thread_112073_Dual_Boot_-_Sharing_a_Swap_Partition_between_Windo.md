---
title: "Dual Boot - Sharing a Swap Partition between Windows XP and Breezy Badger"
date: 2006-01-03
forum: Desktop Environments
---

### Post by ColdClone on 2006-01-03
Questions:
Q1: Does anyone know if you can share the swap partion created by Breezy Badger installer between Windows XP and Breezy Badger? (When I boot into XP, I want XP to use that partition for its swap, and when I boot into Breezy Badger, I want it using the same partition for its swap file.)
Q2: What file formating options should be chosen in the Breezy Badger Installer for this swap partition?
Q3: Will these partition formatting options cause the swap partition to operate slower for either OS?
Q4: When I restart the computer, does all data and files in that partition get erased (leaving it free for another OS to use it)?
Q5: Will it be free space if the system power is just cut while either OS is running?


Install Notes:
I first booted off Windows XP CD and erased all partitions.
I created a new 27GB partition and formated it NTFS for Windows XP
I finished installing Windows XP to this partition.
I then booted off the Breezy Badger CD.
I created a 1GB partition for the swap to possibly use with both OSs (one at a time naturally).
I created a 27GB partition and formatted it Ext3 with the boot flag for Breezy Badger.
I created a 5GB partition and formatted FAT32 for use by both OSs.

System Description:
Dell Inspiron 8000 Laptop (01/01/2001)
PIII 800 Mhz
512RAM
60GB HDD
1600 x 1200 LCD
32MB ATI Mobility M4 Graphics Card
Sony 8X CD-RW
Toshiba 8X DVD-ROM

- Any help would be much appreciated !

---

### Post by art on 2006-01-03
Win XP uses a swap file not a swap partition as far as I know

---

### Post by ahave2005 on 2006-01-03
Q1 - Not as far as I'm aware of.
> Swap space must be formatted for use as swap space, but it is not generally considered a filesystem, otherwise.
Source: [https://www6.software.ibm.com/developerworks/education/l-lpic1104/section2.html](https://www6.software.ibm.com/developerworks/education/l-lpic1104/section2.html)

For XP to be able to read and write to the pagefile, the partition on which it resides, needs to be either Fat32 or NTFS.

I doubt Linux would be able to use Fat32 as a swap partition, and even more unlikely NTFS, since that's not really supported by Linux. Linux reads but only experimentally writes to NTFS, and its not recommended to try on a partition, where you have data you dont want to corrupt.

/ahave

---

### Post by mztriz on 2006-01-03
watch this video, mabye it will help ;) 
[http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu](http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu)

---

### Post by kingsidy on 2006-01-03
not that i know of. i think that xp uses a pageline within the partion not a separate one. therefore i do not think that it is possible to share that.

---

### Post by ColdClone on 2006-01-03
Thank you everyone. This poses a new important question:

Q1: Will Windows XP run faster if you put its swap file (page file) on a seperate dedicated NTFS partion (create a new NTFS partition with Windows XP Install Disk). 

Q2: Is there anything else I can do to speed up Windows XP?

(other than defrag, emptying junk files, installing minimal software, keeping most of the HDD free, running low resource virus protection, keeping it up to date with windows update patches, running Lavasoft's Ad-Aware every so often) (and you wonder why i need windows XP at all :)

---

### Post by art on 2006-01-03
[QUOTE=ahave2005]Q1 - Not as far as I'm aware of.

Source: [https://www6.software.ibm.com/developerworks/education/l-lpic1104/section2.html](https://www6.software.ibm.com/developerworks/education/l-lpic1104/section2.html)

For XP to be able to read and write to the pagefile, the partition on which it resides, needs to be either Fat32 or NTFS.

I doubt Linux would be able to use Fat32 as a swap partition, and even more unlikely NTFS, since that's not really supported by Linux. Linux reads but only experimentally writes to NTFS, and its not recommended to try on a partition, where you have data you dont want to corrupt.

/ahave[/QUOTE]


Well, I might be wrong, but giving a link to a password protected website is not really helpful:)

---

### Post by ahave2005 on 2006-01-03
art: You're right about that, I simply forgot I had to log in.

I've have to say though, if you are a linux newbie, it's well worth the effort to register. They have a few very good articles on linux. Apparantly it's made for preperations to the LPI exams. I highly recommend it. But I can see my link is of no use to anyone not interested to register, sorry about that.

As for placing XP's pagefile on a seperate partition. I would say, yes it could speed up things a bit. I'm thinking about the fragmentation that occours after a while. But it's strongly recommended to put the pagefile on another drive, maybe even on another HD controller. The reason for this is, that its faster when XP reads from the installed drive to cache the pagefile on another controller. Ie. IDE0 and IDE1.
/ahave

---

### Post by Suger on 2006-01-03
Apart from uninstalling Windows, you've done everything my computer-savvy-but-XP-running friends have done.

---

### Post by ColdClone on 2006-01-03
Thank You :)
Reassurance is always appreciated.

---

### Post by ColdClone on 2006-01-03
Does anyone know anything about about using seperate RAM plugged into PCMCIA as  a location for a linux swap partition OR a place for the windows swap file (page file). Maybe even a SD or Compact flash chip would work faster than my single internal IDE or a firewire 400 ( I have the Lacie 250GB F.A. Porsche Drive) or USB 2.0 Drive. I have the Extreme III 1GB SanDisk SD Card (20MB/s read/write). I would put the  SD card in a PCMCIA adapter I guess.

Anyone know about PCMCIA RAM or RAM Drives?

Of course, I am stuck with a laptop for now (Manhattan studio = no desktop space), but when i get a desktop (self built), I will make sure it has two SCSI controllers each with an Ultra 320 15K RPM Cheetah drive.

I know about Cenatek and their wonderfully expensive Hardware PC Slot Ram Drives and RAM Disk software. As for the software solution, my laptop is maxed out as 512MB so their RAM disk software would be useless to me

---

### Post by Milflyboy on 2006-03-03
Hey hey! Someone trying to do the same thing! I've searched around some and can answer or half-answer some of those Q's, but I have some of my own as well.

Answers first:
Yes, supposedly it can be done. I found a general [how-to]("http://www.tldp.org/HOWTO/Swap-Space.html") written specifically about RedHat and some Windows (not specifically XP), but you can get a lot from it.

XP allows you to specify what logical drive you want to have your swap file on. MS describes the process [here]("http://support.microsoft.com/default.aspx?scid=KB;EN-US;307886&"). Important Note!: You either have to keep a small page file on C: or forfeit those little memory dumps the Windows kernel does in its dying breath after a fatal error (then asks you to submit to MS upon next startup). When the wheels come off, the kernel can't rely on access to any logical drive other than the one it was loaded from, usually C. Frustrating, but it makes sense. Of course, I've never gotten a reply or seen a patch after all my error reports to MS, so maybe it doesn't do any good anyway! ;)

Just doing that will speed up your swap access a tiny bit, but like ahave said, the optimal place for it is on a non-system physical disk or (even better) an entirely different controller.

I'm doing all this on my laptop, though, so I'm limited to one disk. (I think Windows would die if I moved my swap file to my USB1 drive, but I've considered doing it just to see it. :D) There was only one remaining option: take advantage of the fact that average access time decreases as you move toward the beginning (outer edge) of a physical disk. So I got ahold of Partition Magic 8 and used it to push back the start of my C: partition on the disk and create a new 750MB NTFS partition before it. This can be DANGEROUS, however, if you're not careful!:

Pitfall 1: BIOSes can only access bootloaders within the first 2GB of each physical disk. If you were to move the start of C: beyond the 2 GB mark, you might render Windows unbootable until you moved it back. I'm not totally sure how Linux gets around that 2GB thing. If Linux puts a bootloader at the beginning of the disk for the BIOS to find, wouldn't ntldr go there too if Windows recovetted your machine by overwriting GRUB/LILO? At any rate, I made sure C: started well before the 2GB mark. (Ntldr should be one of, if not THE, first file in C.)

Pitfall 2: Recent Windows versions (post 95/98 for sure, but maybe those too) are anal about being installed on the first non-hidden partition on any physical disk. Partition Magic automatically fooled XP into thinking it IS first by having an improper (but still valid) partition table, one in which the partitions are numbered out of order. Here's my Partition Info report:

```
==================================================
Partition Information for Disk 1:    38,154.4 Megabytes
Volume    PartType    Status    Size MB    PartSect     #     StartSect  TotalSects
==================================================
           SaveToDisk        Pri             23.5            0         0               63           48,132
S:             NTFS             Pri           753.0            0         2         48,195     1,542,240
C:             NTFS       Pri,Boot    20,002.8            0        1     1,590,435   40,965,750
Info: MBR Partition Table not in sequential order.
           ExtendedX        Pri        17,375.0            0        3     42,556,185  35,583,975
           EPBR                 Log       16,629.8        None     --    42,556,185  34,057,800
           Linux Ext3   Log,Boot    16,629.8  42,556,185  0    42,556,248   34,057,737
           EPBR                Log            745.2   42,556,185  1    76,613,985   1,526,175
*:SWAP  Linux Swap    Log            745.2   76,613,985  0    76,614,048   1,526,112 
```
Oh, that's just beautiful. Uhh...moderator? Those are normal spaces that line up in the editing view.

Note that the #2 partition is before the #1 partition in the table in order to satisfy XP.

Like I said, Partition Magic did that for me all on it's own. (Thank God.) Oh! Don't resize an Ext2/3 with PM. Damn thing purports to be totally competent working with Ext partitions, but it doesn't change the partition size in the superblock, when you resize it. Ubuntu wouldn't load from the corrupt partition and I ended up having to just delete and recreate it after the Linux fdisk-equivs refused to work with it. (Who the hell writes a partitioning tool that aborts when it can't find those last inodes that don't actually exist?!)

[Here]("http://www.pcguide.com/ref/hdd/file/part.htm")'s a site with some old but still good explanations about what I just talked about and other stuff like what cluster size to use for a swap partition. Make sure to follow the links to the next pages on that site. It also talks about disabling page file resizing. Those things should optimize your swap for the Windows side of things. The location on the disk will help in any OS.

Now for getting Ubuntu to use that new partition.
Since I haven't actually done this part yet, I can only point you to that first how-to link I gave. Using the same swap partition for Ubuntu and XP doesn't require either one to understand the file system of the other. After the OS shuts down the swap is worthless, just irrelevant data that no longer applies and is overwritten as needed on next boot. So...f**k it! :mrgreen: Create a script that Linux runs early in its boot sequence that quick-formats the partition as Linuxswap! I guess that how-to figures XP couldn't handle putting the seat down for itself (a perfectly resonable assumption) and uses a Linux shutdown script that's simply the reverse of the startup one, leaving an NTFS behind.

I guess I'll go for that if I have to, as I use XP most of the time right now anyway, but when I eventually use Linux most of the time that assymetrical a*s-wiping routine (perhaps I'm getting too metaphorical :)) will be a wasteful nuisance. There's no point in laying down an NTFS on shutdown if you're going to use Linux again the next time. It would be optimal to have each OS check the fs and change it only when necessary when it starts up. Nothing on shutdown for either of them. There's gotta be some way to have XP do this (or run something efficient that will) early in startup. Could GRUB do it before passing things off to ntldr? :-k Any gurus know how to go about doing this?

My second Q: Can Ubuntu handle the creation of a blank NTFS? Without corruption? ;)

---

### Post by Milflyboy on 2006-03-04
[QUOTE=Suger]Apart from uninstalling Windows, you've done everything my computer-savvy-but-XP-running friends have done.[/QUOTE]

Umm, how exactly does that work? :-p

---

### Post by tzc on 2006-12-07
Plan A: Can't you just use FS-Driver to let XP access the Linux drive, rather than have to keep making Ubuntu format the swap partition on starting up and shutting down? I appreciate that XP would otherwise probably get confused if it's swap partition wasn't NTFS (or FAT3) when it started up. But is this possible? I know FS-Driver is newer than this how-to. I'm now running Edgy with ntfs-3g and XP with FS-Driver.

Plan B (simpler): can't XP manage to use a FAT32 swap partition? Presumably older versions of Windows had to do this, so why can't XP? But can Linux use a FAT32 swap partition?

Just a thought. Maybe there's a good reason why not. Thanks for the how-to; and I hope it went well. Maybe you could update this with news? I'd kind of like to use one swap partition for both XP and Linux - but I'm being careful at the moment! I already managed to destroy my Ubuntu installation once. I don't really want to damage either XP or Ubuntu again just now!

I suppose it must be technically possibly to run Linux off almost any alternative file system, unlike Windows - but I can't see why you'd choose NTFS just for reasons of compatibility with XP: it would be like square pegs in round holes. I'm working myself up to abandoning Windows anyway...

---

### Post by tzc on 2006-12-07
In answer to my own question, see [http://www.fs-driver.org/](http://www.fs-driver.org/) for the fact that the Windows XP page file can indeed be put on a Linux volume. Thus the theoretical need for a FAT3 swap partition oulined above (I have no idea if that is even possible) is no more. Problem solved! Hopefully this will speed up Windows and avoid such terrible fragmentation problems as it traditionally has. Anybody know if it affects that at all?

---

### Post by pavallokazzo on 2008-03-01
How about to mount the windows swap file as a loopback device?
Anybody can suggest?

---


---
title: "Help! i cant find windows!"
date: 2008-08-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dwid717 on 2008-08-31
I am currently running the Live CD and i am a COMPLETE n00b when it comes to partitions, bootloaders, and all that...

someone please help me! is everything gone? or can i just not access it...

here is some info from gparted:

[HTML]GParted 0.3.5

Libparted 1.7.1

Check and repair filesystem (fat16) on /dev/sda1  00:00    ( ERROR )
     	
calibrate /dev/sda1  00:00    ( SUCCES )
     	
path: /dev/sda1
start: 63
end: 153244034
size: 153243972 (73.07 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:00    ( SUCCES )
     	
dosfsck -a -w -v /dev/sda1
     	
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "Dell 8.0"
Media byte 0xf8 (hard disk)
512 bytes per logical sector
2048 bytes per cluster
1 reserved sector
First FAT starts at byte 512 (sector 1)
2 FATs, 16 bit entries
40448 bytes per FAT (= 79 sectors)
Root directory starts at byte 81408 (sector 159)
512 root directory entries
Data area starts at byte 97792 (sector 191)
20017 data clusters (40994816 bytes)
63 sectors/track, 255 heads
63 hidden sectors
80262 sectors total
Reclaiming unconnected clusters.
/dev/sda1: 87 files, 3872/20017 clusters
grow filesystem to fill the partition  00:00    ( ERROR )
     	
using libparted
libparted messages    ( INFO )
     	
File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 20017 (39957 expected); size of FATs is 79 sectors (157 expected).[/HTML]

Thanks in advance, everyone...

-Mike

---

### Post by Elric27 on 2008-08-31
Hi. Windows should be on the first partition, if more than one, and its own bootloader is on the mbr. What you do is to create a new partition with gparted (at least 10gb) and overwrite the mbr with grub, so you can dualboot. Grub will detect other os upon installation, let it get installed on the mbr, though ist config files will be stored on the ubuntu partition, and be configured by itself. Don't be afraid of wrecking windows, as far as you don't overwrite it. Use the manual partition and select the one you create for ubuntu.

---

### Post by BurkDP on 2008-08-31
TestDisk - [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

If you accidently delete your partition.

Bootable live CD. I accidently deleted a rather important partition on an external drive, and had that moment of creeping horror as I realized what I did.

This fixed it. 

Like magic.

If I saw a developer I'd kiss them. :tongue:

"TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting a Partition Table). Partition table recovery using TestDisk is really easy."

TestDisk can

Fix partition table, recover deleted partition
Recover FAT32 boot sector from its backup
Rebuild FAT12/FAT16/FAT32 boot sector
Fix FAT tables
Rebuild NTFS boot sector
Recover NTFS boot sector from its backup
Fix MFT using MFT mirror
Locate ext2/ext3 Backup SuperBlock
Undelete files from FAT filesystem
Copy files from deleted FAT, NTFS and ext2/ext3 partitions.

TestDisk has features for both novices and experts. For those who know little or nothing about data recovery techniques, TestDisk can be used to collect detailed information about a non-booting drive which can then be sent to a tech for further analysis. Those more familiar with such procedures should find TestDisk a handy tool in performing onsite recovery.

---

### Post by dacorr on 2008-08-31
is it windows vista?

if so it may not display the partition as vista maintains its own partition table outside of the MBR

---

### Post by BurkDP on 2008-08-31
I'm still new myself, but I was running it under Vista to recover a partition on an external drive that I had partitioned/formatted/and then accidently deleted with Vista so it might work. I guess. I dunno. Can't hurt to try...as long as you don't get too overeager hitting the write changes button.

---

### Post by dwid717 on 2008-08-31
i was running XP... im going to give this a try... i'll keep you all updated, thank you so much!

-Mike

---

### Post by dwid717 on 2008-08-31
ok, i guess im more of a n00b than i thought...

if im running ubuntu, do i download Linux, kernel 2.6.x i386/x86_64, tar.bz2 or
Linux, kernel 2.4.x i386/x86_64, tar.bz2 ??

and once i download them, i have NO idea what to do with them... HELP!

-Mike

---

### Post by BurkDP on 2008-09-01
It just might be easier to burn and run the live CD. There should be instructions on burning an .iso on the wiki. I don't know to to much about using the program, but I would think if you're messing with your boot disk it'd be better to run the live CD.

If you really want to install the binaries, you know in case you need to rescue another external disk, type

uname -r

into the terminal. It should print something like "2.6.24-19-generic".

And sorry if this is a little late - the subscription email update never came.

---

### Post by BurkDP on 2008-09-01
Well, after looking at the download page it turns out the package is in the repository... eheheheh...and here I was so proud of myself for figuring out how to compile it when the given instructions didn't work...

[[COLOR="Blue"]Ubuntu packages search for "testdisk"[/COLOR]]("http://packages.ubuntu.com/search?keywords=testdisk")

So just fire up synaptic or sudo apt-get install testdisk.


But still, here's a good Live rescue CD. I'd still think this would be the way to go if your Windows partition is on the same Hard Drive that you're running linux from.

[[COLOR="Blue"]Ubuntu Rescue Remix[/COLOR]]("http://ubuntu-rescue-remix.org/")

It boots to a console but just type in "testdisk". It's easy enough to use.

BTW, TestDisk always installs with it's companion program Photorec which is for getting deleted images off of a camera memory card.

---

### Post by Twitster on 2008-09-01
> **dwid717 said:**
> ok, i guess im more of a n00b than i thought...

if im running ubuntu, do i download Linux, kernel 2.6.x i386/x86_64, tar.bz2 or
Linux, kernel 2.4.x i386/x86_64, tar.bz2 ??

and once i download them, i have NO idea what to do with them... HELP!

-Mike

We need to know your architechture. Firstly, don't bother with 2.4.X for anything. It's not really used anymore. 2.6 has the latest editions. Anyway, do you know if your computer has a 64bit processor? It would usually say it on the front of the box. 
Post back with if it's a 64 bit, info on your processor, or whatever data you can come up with and I'll see if I can help.
We need to know your architechture, because processors can either be 32 bit or 64 bit. Mixing the kernel with the wrong architechture is just not going to work.

---

### Post by BurkDP on 2008-09-01
Well the package has "X86_64" in it's name so I'd just assumed it works for both (although you know what they say when you assume). I have installed that particular package on my amd64 and it runs, although I haven't tried to fix a disk.

They do have it in the repositories for a much easier install though. It's not too out of date. It is in the [[COLOR="Blue"]universe repository[/COLOR] ]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20the%20Universe%20and%20Multiverse%20Repositories")though.

Still, it sounds like the disc he's trying to fix is the his primary hard drive and not an extra drive. I may be a fledgling user and not know much, but burning a [[COLOR="Blue"]Ubuntu Rescue Remix[/COLOR]]("http://ubuntu-rescue-remix.org/") live cd and running TestDisk sounds like the easiest way.

I wish I had known this when openSUSE ate my parent's Vista partition while I was playing with it. I had the CD all burned but no idea how to use and had to do a full on reinstall. Not as painful as reinstalling XP would be though...sooo many updates.


It's not a shameless plug, but a friend recently gave me some space on his domain and set me up with a wiki. It's fairly empty but I was planning on amalgamating together all of the various information I've been learning through attrition and how-tos I've found on the web. I have a page up on TestDisk, but it's not much about how to use it I'm afraid. Not even updated to the information in my posts....

[[COLOR="blue"]Burkpedia: TestDisk[/COLOR]]("http://burk.crabula.com/index.php?title=TestDisk")

---

### Post by BurkDP on 2008-09-01
This might also help (from the ubuntu rescue remix documentation)
[URL="http://ubuntu-rescue-remix.org/node/57"][COLOR="Blue"]
Repair NTFS Boot Sector[/COLOR][/URL]

It's a brief description of how to use TestDisk.

---


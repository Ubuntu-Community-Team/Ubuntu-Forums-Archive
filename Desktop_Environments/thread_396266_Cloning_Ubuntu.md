---
title: "Cloning Ubuntu"
date: 2007-03-29
forum: Desktop Environments
---

### Post by Weaseal on 2007-03-29
Does anyone have any suggestions for how to best go about cloning an Ubuntu installation?  I've got 1 comp set up, and now I want 8 others to have the same thing, without having to repeat each step on every computer.

PS: These computers all currently have Windows, except the Ubuntu one, which is dual-booting Windows and Linux.  They all need to be able to dual boot.  I've already taken care of all the drive formatting myself.

---

### Post by AlanRogers on 2007-03-29
PartImage (Linux equivalent of Norton Ghost) to take an image of the drive or partitions and then drop these on the other machines? Of course, you'll lose any data on those machines in doing it this way, unless you've already backed it up.

---

### Post by Weaseal on 2007-03-29
Can anyone tell me how they feel about this approach?

What if I run the Ubuntu Live CD and then copy the previously set up computer's linux partition entirely onto the new drive, and then make the appropriate changes to /etc/fstab (assuming there are any) and grub.  Yea or nea?

---

### Post by AlanRogers on 2007-03-29
> **Weaseal said:**
> What if I run the Ubuntu Live CD and then copy the previously set up computer's linux partition entirely onto the new drive, and then make the appropriate changes to /etc/fstab (assuming there are any) and grub.  Yea or nea?I'm no expert but I suspect this method will be slower than dropping an image onto the drive and rebooting, because you copying a lot more data.

---

### Post by 900i on 2007-03-29
You need remastersys

[http://linuxmint.com/wiki/index.php/Remastersys](http://linuxmint.com/wiki/index.php/Remastersys)

---

### Post by Smuve on 2007-03-29
I'm no expert, but I just discovered and used partimage last night.  It is amazingly easy.  You tell it what drive you want to copy i.e. /dev/hda1 and it copies it to an image file ie. hda1.img  It's as simple as that.

Then you could boot up the other pc via live cd, install partimage and use it to restore the hda1.img file to the new pc's partition.

I haven't tried it, but it looks easy as can be.  I just backed up a drive I'm going to reformat (from FAT32 to ext3), then restore the image back onto it using the new file system.

---

### Post by stavpal on 2007-03-30
I have an important question about Norton Ghost (or it could be "what backup program to use".)
In the last 2 days I have spent 10hours and 4 dvd discs to the junk (bin) trying to make a backup of my partition - nah....every time the backup didn't go well and I had to reinstall linux from scratch.
I have the nt-loader in the 1st (and only) primary partition (fat32 520mb). Few other partitions are ntfs (win2003, winxp, documents etc) and final 3 partitions (ext3) are ubuntu, (swap), linux documents


My ubuntu partition is 60gb (used ~3gb)
When I tried to restore the image I had created (on a dvd+r) I always got an  error:
```

*********************************

Date   : Fri Mar 30 18:36:28 2007

Error Number: (31011)

Message: Unexpected packet type: found 3, expecting file data



Version: 2003.789 (May 28 2003, Build=789)

Command line arguments:

Active Switches :

       Spanning

       AutoName

ProgMode            : PROG_LOCAL

PathName            : 

DumpFile            : E:\CDR00001.GHO

DumpPos             : 625983009

File64 buffersize   : 32768

FlagImplode         : 0

FlagExplode         : 0



Operation Details :

  Total size.........2713

  MB copied..........608

  MB remaining.......2105

  Percent complete...22%

  Speed..............128MB/min

  Time elapsed.......4:45   

  Time remaining.....16:24   



Program Call Stack

Generic_Abort

ReadData

WritePindBlock

WriteDindBlock

RestoreExt2File

RestoreExt2Node

RestoreExt2FileSystem

CopyLinuxPartition

ProcessLinuxPartition

CopyPartition

CopyFileToPart

CopyMainline

AttemptOperation

sub_main

main



Call Stack

  0x0023b6a7

  0x0006b0bf

  0x0006a36c

  0x0006a1e1

  0x0006b843

  0x000b53b0

  0x000b555d

  0x000b577c

  0x000b6880

  0x000b6abe

  0x000b700c

  0x000b72fb

  0x000b7b5e

  0x0002d8b9

  0x0002c875

  0x000022f5

  0x000023f3

  0x00004426

  0x0000370b

  0x00248da8

End Call Stack





Start heap available: 531038208

Cur   heap available: 459669504

Total Memory:         535691264



Conventional Memory

Inital Conventional Memory Size = 395248

Current Conventional Memory Size = 260080

Allocated

   1024 DpmiDjgpp.cpp:59

  33504 ghost.cpp:913

    528 IdeDmaServerPci.cpp:132

    528 IdeDmaServerPci.cpp:132

     32 DiskDriveAccessExInt13.cpp:107

    512 DiskDriveAccessExInt13.cpp:107

  32768 file64.cpp:298

Free

     16 MsdosFile.cpp:92

     80 DiskDriveAccessExInt13.cpp:93

    512 DiskDriveAccessInt13.cpp:176

   1024 DiskDriveAccessExInt13.cpp:217



Fat details:

  SRC:

  FatType..........32

  first_sect.......63

  ClusterSize......512

  clusters.........1043875

  root_next_avail..0

  data_next_avail..0

  dir_sector.......0

  root_sector......16352

  data_sector......16352

  FAT_sector.......0



NTFS details:

----------------



NTFS Global Flags:

----------------

	 contiguousWrite=1 forceDiskClusterMapping=0 

	 inhibitCHKDSK=1 ignoreBadLog=0 ignoreCHKDSKBit=0

	 enable_cache=0 xfrbuflen=0 

	 last_attr_type = 0 

----------------

	=======================================================

	NTFS volume 0:

	----------------

	initialised..............1

	read cached..............N

	Selective caching........N

	flags....................Volume OK

	drive....................0x00

	part order...............5

	version..................0x0400

	volsize..................30732280

	blocksize................512

	clusterfactor............8

	clustersize..............4096

	mftrecordsize............1024

	indexrecordsize..........4096

	indexclustperrecord......1

	bootSectorCopyOffset.....30732280

	pagefileSys..............4294967295

	bootIni..................4294967295

	volumeLabel..............[VARIOUS]

	sectorsInUse.............23306216

	totalNonCopiedBytes......0

	bytesToCopy..............0

	bitmapClusters...........118

	bitmapUsedBytes..........480192

	estimatedClusters........118

	estimatedUsedBytes.......480192

	clustersizeShift.........12

	blocksizeShift...........9

	mftrecordsizeShift.......10

	indexrecordsizeShift.....12

	totalRootMftRecs.........0

	clustermap failover......N

	Boot sector details

		name....................[NTFS    ]

		blocksize...............512

		clusterfactor...........8

		reservedSectorsUnused...0

		mediaType...............0xf8

		secPerTrack.............63

		numHeads................255

		hiddenSectors...........63

		volsize_lo..............30732280

		volsize_hi..............0

		mftcluster.(lo).........4

		mftcluster.(hi).........0

		mftmirrorcluster.(lo)...524288

		mftmirrorcluster.(hi)...0

		clustersPerMFTRecord....246

		clustersPerIndexBuffer..1



		---------------------------------------------------

		Cluster Allocation Map

		---------------------------------------------------

		Start:   3841535 Length:         0 Next:   3841535





	=======================================================

	=======================================================

	NTFS volume 1:

	----------------

	initialised..............1

	read cached..............N

	Selective caching........N

	flags....................Volume OK

	drive....................0x00

	part order...............4

	version..................0x0400

	volsize..................8594704

	blocksize................512

	clusterfactor............8

	clustersize..............4096

	mftrecordsize............1024

	indexrecordsize..........4096

	indexclustperrecord......1

	bootSectorCopyOffset.....8594704

	pagefileSys..............4294967295

	bootIni..................4294967295

	volumeLabel..............[DOCUMENTS]

	sectorsInUse.............6962120

	totalNonCopiedBytes......0

	bytesToCopy..............0

	bitmapClusters...........33

	bitmapUsedBytes..........134296

	estimatedClusters........33

	estimatedUsedBytes.......134296

	clustersizeShift.........12

	blocksizeShift...........9

	mftrecordsizeShift.......10

	indexrecordsizeShift.....12

	totalRootMftRecs.........0

	clustermap failover......N

	Boot sector details

		name....................[NTFS    ]

		blocksize...............512

		clusterfactor...........8

		reservedSectorsUnused...0

		mediaType...............0xf8

		secPerTrack.............63

		numHeads................255

		hiddenSectors...........63

		volsize_lo..............8594704

		volsize_hi..............0

		mftcluster.(lo).........4

		mftcluster.(hi).........0

		mftmirrorcluster.(lo)...524288

		mftmirrorcluster.(hi)...0

		clustersPerMFTRecord....246

		clustersPerIndexBuffer..1



		---------------------------------------------------

		Cluster Allocation Map

		---------------------------------------------------

		Start:   1074338 Length:         0 Next:   1074338





	=======================================================

	=======================================================

	NTFS volume 2:

	----------------

	initialised..............1

	read cached..............N

	Selective caching........N

	flags....................Volume OK

	drive....................0x00

	part order...............3

	version..................0x0400

	volsize..................61448560

	blocksize................512

	clusterfactor............8

	clustersize..............4096

	mftrecordsize............1024

	indexrecordsize..........4096

	indexclustperrecord......1

	bootSectorCopyOffset.....61448560

	pagefileSys..............4294967295

	bootIni..................4294967295

	volumeLabel..............[GAMES]

	sectorsInUse.............50770736

	totalNonCopiedBytes......0

	bytesToCopy..............0

	bitmapClusters...........235

	bitmapUsedBytes..........960136

	estimatedClusters........235

	estimatedUsedBytes.......960136

	clustersizeShift.........12

	blocksizeShift...........9

	mftrecordsizeShift.......10

	indexrecordsizeShift.....12

	totalRootMftRecs.........0

	clustermap failover......N

	Boot sector details

		name....................[NTFS    ]

		blocksize...............512

		clusterfactor...........8

		reservedSectorsUnused...0

		mediaType...............0xf8

		secPerTrack.............63

		numHeads................255

		hiddenSectors...........63

		volsize_lo..............61448560

		volsize_hi..............0

		mftcluster.(lo).........4

		mftcluster.(hi).........0

		mftmirrorcluster.(lo)...524288

		mftmirrorcluster.(hi)...0

		clustersPerMFTRecord....246

		clustersPerIndexBuffer..1



		---------------------------------------------------

		Cluster Allocation Map

		---------------------------------------------------

		Start:   7681070 Length:         0 Next:   7681070





	=======================================================

	=======================================================

	NTFS volume 3:

	----------------

	initialised..............1

	read cached..............N

	Selective caching........N

	flags....................Volume OK

	drive....................0x00

	part order...............2

	version..................0x0400

	volsize..................271787606

	blocksize................512

	clusterfactor............8

	clustersize..............4096

	mftrecordsize............1024

	indexrecordsize..........4096

	indexclustperrecord......1

	bootSectorCopyOffset.....271787606

	pagefileSys..............4294967295

	bootIni..................4294967295

	volumeLabel..............[win2003R2]

	sectorsInUse.............215290152

	totalNonCopiedBytes......0

	bytesToCopy..............0

	bitmapClusters...........1037

	bitmapUsedBytes..........4246688

	estimatedClusters........1037

	estimatedUsedBytes.......4246688

	clustersizeShift.........12

	blocksizeShift...........9

	mftrecordsizeShift.......10

	indexrecordsizeShift.....12

	totalRootMftRecs.........0

	clustermap failover......N

	Boot sector details

		name....................[NTFS    ]

		blocksize...............512

		clusterfactor...........8

		reservedSectorsUnused...0

		mediaType...............0xf8

		secPerTrack.............63

		numHeads................255

		hiddenSectors...........63

		volsize_lo..............271787606

		volsize_hi..............0

		mftcluster.(lo).........786432

		mftcluster.(hi).........0

		mftmirrorcluster.(lo)...16986725

		mftmirrorcluster.(hi)...0

		clustersPerMFTRecord....246

		clustersPerIndexBuffer..1



		---------------------------------------------------

		Cluster Allocation Map

		---------------------------------------------------

		Start:  33973450 Length:         0 Next:  33973450





	=======================================================

	=======================================================

	NTFS volume 4:

	----------------

	initialised..............1

	read cached..............N

	Selective caching........N

	flags....................Volume OK

	drive....................0x00

	part order...............1

	version..................0x0400

	volsize..................65545136

	blocksize................512

	clusterfactor............8

	clustersize..............4096

	mftrecordsize............1024

	indexrecordsize..........4096

	indexclustperrecord......1

	bootSectorCopyOffset.....65545136

	pagefileSys..............4294967295

	bootIni..................4294967295

	volumeLabel..............[winXPsp2]

	sectorsInUse.............42927920

	totalNonCopiedBytes......0

	bytesToCopy..............0

	bitmapClusters...........251

	bitmapUsedBytes..........1024144

	estimatedClusters........251

	estimatedUsedBytes.......1024144

	clustersizeShift.........12

	blocksizeShift...........9

	mftrecordsizeShift.......10

	indexrecordsizeShift.....12

	totalRootMftRecs.........0

	clustermap failover......N

	Boot sector details

		name....................[NTFS    ]

		blocksize...............512

		clusterfactor...........8

		reservedSectorsUnused...0

		mediaType...............0xf8

		secPerTrack.............63

		numHeads................255

		hiddenSectors...........63

		volsize_lo..............65545136

		volsize_hi..............0

		mftcluster.(lo).........786432

		mftcluster.(hi).........0

		mftmirrorcluster.(lo)...4096571

		mftmirrorcluster.(hi)...0

		clustersPerMFTRecord....246

		clustersPerIndexBuffer..1



		---------------------------------------------------

		Cluster Allocation Map

		---------------------------------------------------

		Start:   8193142 Length:         0 Next:   8193142





	=======================================================



Disk Info :

  remote.............0

  drive..............0

  sectors_used.......565808733

  estimated_used.....132197527

  pemax..............1

  Version............760



 # Ord Boot Id Ext First    Num      Last     Used     NTFS

 0   6    0 83 Yes 439168968 117194112 556363080 05557320 No



Disk Info :

  remote.............0

  drive..............0

  sectors_used.......625136715

  estimated_used.....339351076

  pemax..............9

  Version............0



 # Ord Boot Id Ext First    Num      Last     Used     NTFS

 0   6    0 83 Yes 439168968 117194112 556363080 117194112 No

 1   1    0 7  Yes 01060353 65545137 66605490 42927920 Yes

 2   2    0 7  Yes 66605553 271787607 338393160 215290152 Yes

 3   3    0 7  Yes 338393223 61448562 399841785 50770736 Yes

 4   4    0 7  Yes 399841848 08594712 408436560 06962120 Yes

 5   5    0 7  Yes 408436623 30732282 439168905 23306216 Yes

 6   0   80 b  No  00000063 01060227 01060290 00093932 No

 7   7    0 82 Yes 556363143 03148677 559511820 03148677 No

 8   8    0 83 Yes 559511883 06297417 565809300 06297417 No



Drive 128 WDC WD3200JB-00KFA0      WD-WCAMR1376212



Int 13h

Total Sectors     16450560

Bytes per Sector  512

MB                8032

Cylinders         1024

Heads             255

Sectors per Track 63



Extended Int 13h

Total Sectors     625142448

Bytes per Sector  512

MB                305245



IDE using PIO

Total Sectors     625142448

Bytes per Sector  512

MB                305245

Cylinders         16383

Heads             16

Sectors per Track 63



IDE using UDMA (Active)

Total Sectors     625142448

Bytes per Sector  512

MB                305245

Cylinders         16383

Heads             16

Sectors per Track 63



Drive 129



Int 13h

Total Sectors     16434495

Bytes per Sector  512

MB                8024

Cylinders         1023

Heads             255

Sectors per Track 63



Extended Int 13h (Active)

Total Sectors     234441648

Bytes per Sector  512

MB                114473



Remote Drives

AsyncIo : 0

Image Devices



Key      A:

Path     A:

Desc     

Type     Floppy



Key      C:

Path     C:

Desc     [BOOT]

Type     Disk

Disk     0

Offset   63



Key      D:

Path     D:

Desc     []

Type     CD



Key      E:

Path     E:

Desc     [GHOST_001]

Type     CD



Key      @LFO1:2

Path     1:2

Desc     [winXPsp2]

Type     NTFS

Disk     0

Offset   1060353



Key      @LFO1:3

Path     1:3

Desc     [win2003R2]

Type     NTFS

Disk     0

Offset   66605553



Key      @LFO1:4

Path     1:4

Desc     [GAMES]

Type     NTFS

Disk     0

Offset   338393223



Key      @LFO1:5

Path     1:5

Desc     [DOCUMENTS]

Type     NTFS

Disk     0

Offset   399841848



Key      @LFO1:6

Path     1:6

Desc     [VARIOUS]

Type     NTFS

Disk     0

Offset   408436623



Key      @LFO2:1

Path     2:1

Desc     [BACKUP]

Type     NTFS

Disk     1

Offset   63



Key      @CD-R1

Path     @CD-R1

Desc     HL-DT-STDVD-RAM GSA-H22L

Type     DVD



Key      @CD-R2

Path     @CD-R2

Desc     _NEC    DVD_RW ND-3540A 

Type     DVD





*********************************


```

Can you please tell me what do I need to do in order to make a successful backup (that will fit on a dvd disc)?
(maybe another program)
(It's obvious that I need to restore the image from "dos" or some boot-cd)

---

### Post by ardchoille42 on 2007-03-30
I have 11 computers and I highly recommend the System Rescue CD 

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

It is a live cd with a ton of admin tools, including partimage.

This is how I got Ubuntu on all 11 of my computers:

Set up Ubuntu on one computer
boot into the system rescue cd, on that computer, and make an image of the root partition
burn that partition to a dvd
use the restore function of partimage to drop that image onto the disks of all 10 of the other boxes.

Imaging my main box too about 8 minutes to image the 3Gb root partition - partimage only copies the used bits of a drive rather than the entire disk. Partimage compressed my 3Gb partition down to about 800Mb.

Restoring that image to the other boxes took about 7 minutes per disk.

Partimage is great and I would be totally lost without the system rescue cd.

---

### Post by jmvidalvia on 2007-03-30
Does it also work if you have different partitions in the drive?
I didn't find out how to make the image of the entire disk (including all partitions)!
Thank you very much!

---

### Post by locutus42 on 2007-03-30
here's an option: Install VMWare on one networked computer and then install the Personal Backup Appliance( PBA ) VM from here:

[http://www.vmware.com/vmtn/appliances/directory/321](http://www.vmware.com/vmtn/appliances/directory/321)

When you run this, it boots Ubuntu Server in the VM sharing eth0 with the VM which uses DHCP to get it's own IP address. You'll see the VMs IP address during the boot process of the VM and you use this to browse to the VMs web page to get the bootable ISO image file you'll use in the first/default computer for backup.

It might sound complicated but it's really pretty easy. you have one computer acting as a server running the PBA in a virtual machine. You browse to the web server in the virtual machine and it'll give you a link to the bootable ISO file you then download and burn to a CD. After you've installed Ubuntu or anything else on the target computer, you then reboot that computer using the PBA Client CD. It'll prompt you for the IP address of the PBA server and after entering that, it'll prompt to if you want to backup or restore. Pick "Backup" the first time and it'll send your HD image over the network to the PBA server. when done, connect your next computer to the network, insert the PBA Client CD and when prompted, select "Restore" and when done, you'll have an exact copy of the originally backed up computer.

The problem you might have is that you're going to end up with all the Windows partitions getting copied too.  Microsoft probably won't like that since any hidden codes or whatever to uniquely identify the computer won't be unique anymore. There might be a way to save and restore the license numbers before and then after the "restore" but I can tell you that after a Ubuntu installation on a 10G drive, the restore took less than 5 minutes. So far, I've imaged 4 computers like this and it is pretty cool and quite fast.  I used an old DLink router to create the fake network and it hands out the IP addresses via DHCP so it was a snap.

---

### Post by stavpal on 2007-03-31
Can I use partimage to backup straight to dvd? (I don't have enough free space on other partitions)

---


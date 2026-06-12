---
title: "hard drive performance problems"
date: 2009-02-17
forum: General Help
---

### Post by xianthax on 2009-02-17
i've been having some curious hard drive performance wondering if anyone had a recommendation on how to approach the issue...

relevant hardware:

asus P5E WS motherboard (intel ICH9R south bridge)
Intel Q6600 @ 3.4ghz (core temps of 42c)
4GB ram
150 GB WD raptor mounted at / (this is the drive with a problem, attached to the ICH9R)
3ware 9550 SXU raid controller (4 lanes, PCI-X) 4 x WD RE series 320GB, raid 5 (3 active 1 HS)
ubuntu 8.10 32bit


Symptoms:

Copying ~1GB files from drive mounted at / (the WD raptor) to a another drive mounted at /mnt/data (the raid array) i see a max of 7.5mb/sec, starting multiple transfers sees a sum of 7.5mb/sec.  during this transfer my system is all but unusable, anything that tries to access the the drive that is being read from locks up hard (turns grey) for a minute or more at a time since this is mounted at / this means most apps like firefox eat it.  I also note that LED activity for that drive really  low, as if the drive isn't working very hard, i.e. something in software is causing a problem, given the hardware i have this really shouldn't be happening.  

Also i doubt the write performance of the RAID array is an issue, as activities involving files on this drive show no issue, for instance i can watch a movie, copy files off this drive through nfs, etc WHILE copying files on to this drive and i see the same 7.5MB/sec transfer speed off the raptor.  i've briefly played with writing from the raptor to other devices and the same problem seems to exist universally.

hdparm shows what i would expect for performance numbers for both drives (sdc = raptor, sdd = raid)

```
xianthax@xian:~$ sudo hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   5572 MB in  2.00 seconds = 2786.95 MB/sec
 Timing buffered disk reads:  242 MB in  3.02 seconds =  80.11 MB/sec
xianthax@xian:~$ sudo hdparm -tT /dev/sdd

/dev/sdd:
 Timing cached reads:   5874 MB in  2.00 seconds = 2938.86 MB/sec
 Timing buffered disk reads:  360 MB in  3.01 seconds = 119.47 MB/sec
```

and nothing catches my eye in the information output for the raptor:

```
xianthax@xian:~$ sudo hdparm -I /dev/sdc

/dev/sdc:

ATA device, with non-removable media
	Model Number:       WDC WD1500ADFD-00NLR5                   
	Serial Number:      WD-WMAP41825371
	Firmware Revision:  21.07QR5
Standards:
	Used: ATA/ATAPI-7 published, ANSI INCITS 397-2005 
	Supported: 7 6 5 4 & some of 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  293046768
	device size with M = 1024*1024:      143089 MBytes
	device size with M = 1000*1000:      150039 MBytes (150 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 0
	Recommended acoustic management value: 128, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	Power-Up In Standby feature set
	   *	SET_FEATURES required to spinup after power up
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Phy event counters
	    	DMA Setup Auto-Activate optimization
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
	not	supported: enhanced erase
Checksum: correct

```


any ideas on a solution to this issue? 

EDIT: no CPU usage spiking is seen during the transfer, any apps loaded in memory run along just fine, i just get insane I/O wait times during the transfer

cheers,

x

---

### Post by handy on 2009-02-17
You may do better over in the Server Platforms sub-forum, I'll ask a mod' to move this thread.

---

### Post by fjgaude on 2009-02-18
With these fast CPUs it seems I/0 waits turn into our bottleneck.

Do you **iotop** to measure the speed of the I/O? what?

What does System Monitor show during times of "greying"?

Here's what I get from an overclocked dual E8400:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v: 4x raid5 Seagates

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

You can see that your cached reads are a little slow, eh? I wonder why?

Let us know if you find anything out.

---

### Post by xianthax on 2009-02-18
thanks for the responses.

some new testing...

first i rebooted, system had been up for a month or so, which "magically" fixed some of the issue i guess....

transferring a single 1GB file from the raptor to the raid array yielded ~60MB/sec which seems reasonable to me (watching in iotop)

transferring a single 1gb file from the raid array to the raptor resulted in ~70mb/sec which also seems about right?

here was the odd one if i started multiple transfers of 1GB files (tested with 6 transfers) at first the individual transfer rates added up to roughly 40mb/sec which is reasonable i guess given the above performance.  the odd bit is that as transfers finish, the remaining transfers do not speed up, they stay at ~8mb/sec until they all complete.     

next time i can get the first bug to trigger, i'll take some more data on it.

cheers

---

### Post by fjgaude on 2009-02-19
Consider what effect a big cache of memory may have on thruputs... I/O has so much to do with drive seek times, as the heads have to go over so much territory to get to the next piece of data... that's why SCSI drives are still used for the main online store, and SATA used only for near-line and off-line.

With SATA we are fighting that 9 msec seek time versus the 4.5 of SCSI... for multifile transfers that makes a difference.

---

### Post by xianthax on 2009-04-23
bumping this back up as the problem persists and has gotten worse...

seeing peak reads off the raptor after a fresh reboot of ~5 to 13MB/sec, transferring large files, 300MB to 2GB per file, measuring with iotop. my system is basically unusable during the transfer, everything moves in lock step, windows grey out and come back, etc. 

hdparm shows the same performance as before for both disks, roughly 80-90mb/sec read off the raptor and ~125mb/sec off the 3ware raid array.

i tend to use the raptor as scratch space when working on files before transferring them to the raid volume, which results in the raptor getting lots of writes up to about 80% of its capacity then getting flushed down to ~30% when the files are moved off to the raid volume, my only thought is that this is somehow enough to cause fragmentation on the drive, its formatted as ext3 and realize this generally means that fragmentation is not an issue but perhaps my work load is affecting it.  during a sequential read on a large file the drive does sound busy, quite busy, like the head is jumping around a lot.

full 70 minute offline SMART test of the raptor came back clean as well.  not sure where to head from here but the speed of the drive is starting to effect everything as even loading apps at 10mb/sec, well, sucks...

@fjgaude when the system is bogged down by a transfer i see 0.0% IO waits from iotop, in fact i've never, under any load, seen iotop report anything except 0.0% for IO wait or SWAPIN.  no CPU spikes during grey times.

the difference in burst speed is most likely a caching issue, i didn't see a hardware raid controller in your post, if your using software raid your cache mechanism for the raid device exists in system ram.  also your connections to the sata controller and thus the drives cache is pretty fast (limited by north bridge south bridge link i would think).  In my case i have a PCI-X link @ 1.06 GB/s max to to controller where the raid device cache exists then sata links to the drive caches.  i also don't know enough about how hdparm works to know if the OS can effectively cache for the reads it does.

any thoughts on a solution to this or anything further i can test? with 9.04 out i'm considering the upgrade and moving the raptor (and raid) to ext4 and running the ext4 defrag on the raptor.  any opinions on the likely hood that this may solve the problem?

---

### Post by xianthax on 2009-04-23
upon further investigation and locating the tool filefrag i've found that many files on the raptor seem to be _very_ fragmented...

a random smathering of the most recent 500mb files i've been working on shows roughly this:

5242 extents found, perfection would be 5 extents

all are spread across around 5000 extents with perfect being 5-6

i took a 2.0GB file and wrote it to the raptor, which was only 35% full, 86GB free

2230 extents found, perfection would be 17 extents

took the same file and copied it back to the raid array, which was 94% full, 30GB (did get 45mb/sec, at least its better)

17 extents found

seems the raptor definitely is having fragmentation problems...

given this is there any other option but to upgrade to ext4 to run a defrag on the raptor?

cheers,

xian

---

### Post by fjgaude on 2009-04-23
Well, I do hope 9.04 with ext4 has the ability to defrag, but I'm not sure from what I read.

What you do with the raptor could have something to do with fragmentation... you are pushing things to there limit. I never fill a drive past 80% its capacity. If were doing what you seem to be doing I'd offload the contents of the raptor to another drive, re-filesystem it, and see if that helps... by doing this you start with a clean disk and then see if the thruput is what you think it should be.

Remember, copying to a disk requires the CPU to create new file, open it, and then copying the new data, close it, and then go to the next task.

I personally have little issue with disk I/O because all my work, after a little bit, is in RAM cache, so everything is fast.

You might like to read what is going on with the kernel and such with the comments coming from Linus Toralds, the main man:

[http://www.linux-mag.com/id/7313/](http://www.linux-mag.com/id/7313/)

I/O Wait is always an issue for those doing multitasking with multiple users.

---

### Post by xianthax on 2009-04-23
i've been reading around and believe that the way the apps i use write files to the system could be effecting it as well, i've been doing a TON of video encoding lately in the process of moving my dvd collection to disk in h.264, seems that these encoders start with a very small file size and generally just grow the file as they go, that is they don't know the final file size (they way i use them) and assume that therefore they can't pre-allocate the space needed, i imagine this is almost a worst case scenario for for fragmentation especially as the disk fills up.  i found lots of complaining from the bittorrent crowd about a similar problem as they have a similar write pattern also causing fragmentation issues, with newer clients doing pre allocation to avoid the issue, interestingly the version on transmission in 8.10 does not do pre allocate so be ware...

i've also been looking for information to see if the 9.04 kernal has support for e4defrag without finding a definite answer....

the best answer i suppose is that i need more space anyway, so perhaps its time to just bite the bullet on some more drives for a software raid 5 (thinking of 4 x 1TB given the prices atm) in which case i'd move data store to that array, lose the raptor and redo the 3ware array as /

cheers,

xian

---

### Post by fjgaude on 2009-04-23
Have fun!

---

### Post by xianthax on 2009-04-23
just to further litter this thread with ramblings....

if i went with a new raid, it would be a software (mdadm) raid 5 array with 4 drives..

i would like to create this as a ext4 volume from the start, this means:

1) upgrade current system to 9.04
2) setup new raid, format to ext4
3) copy data over to new raid
4) remove old drive mounted @ / (raptor)
5) wipe 3ware raid, install new 9.04 install to this array
6) setup new OS install to see new software raid....

step 6 is what i have concerns about...is there a particular config file i should back up such that mdadm can figure out which drive is which or is it smart enough to just "figure it out" if i tell it to make a raid 5 array out of the 4 drives which were already setup?  also i'll be moving from 32bit to 64bit OS in the process, does this have any impact on software raid migration? (would think not but eh)

i also have a mdadm raid 1 array with dm-crypt that stores more sensitive work files that i'll have to migrate over, i'm fine with the dm-crypt migration bit but the array itself i suppose has the same question as the new raid5 would have.

cheers,

xian

---


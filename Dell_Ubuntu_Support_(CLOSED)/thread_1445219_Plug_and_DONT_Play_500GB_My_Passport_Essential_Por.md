---
title: "Plug and DONT Play 500GB My Passport Essential Portable Hard Drive USB 2.0"
date: 2010-04-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by curtyc on 2010-04-02
Hi

I'm using an external Western Digital Passport 500GB HDd bought from Dell store (500GB My Passport Essential Portable Hard Drive USB 2.0 Midnight Black, Western Digital Part# WDBAAA5000ABK-NESNBN, Dell Part# A3328581) last year and (as every time for me with Dell store) I had a surprise:

I just want a clear 500 GB HD to put what I want to, when I want to, and the way I want to.
But they sent that to me (sd command) one HD:

	/dev/sr0                456948    456948         0 100% /media/cdrom0
	/dev/sdb1            487700444  81271596 406428848  17% /media/My Passport
	/dev/sr1                456948    456948         0 100% /media/WD SmartWare

that has 2 cd-rom partitions (sr0 and sr1) and 1 hd partition (sdb1), where fdisk command shows:

	Unable to open /dev/sr0	

and
	Disk /dev/sr1: 700 MB, 700448768 bytes
	255 heads, 63 sectors/track, 21 cylinders
	Units = cilindros of 16065 * 2048 = 32901120 bytes
	Disk identifier: 0x241be622

and

	Disk /dev/sdb1: 499.4 GB, 499405258752 bytes
	255 heads, 63 sectors/track, 60715 cylinders
	Units = cylinders of 16065 * 512 = 8225280 bytes
	Disk identifier: 0x69205244
	
	This does not look like a partition table
	Probably you selected the wrong device.
	
	Device Boot Start End Blocks Id System
	/dev/sdb1p1   ?       13578      119522   850995205   72  Unknown
	Partition 1 does not end on cylinder boundary.
	/dev/sdb1p2   ?       45382       79243   271987362   74  Unknown
	Partition 2 does not end on cylinder boundary.
	/dev/sdb1p3   ?       10499       10499           0   65  Novell Netware 386
	Partition 3 does not end on cylinder boundary.
	/dev/sdb1p4          167628      167631       25817+   0  Empty
	Partition 4 does not end on cylinder boundary.
	
	Logical partitions not in disk order

and another one plug and DON'T Play. So I want to clear both the entire disks, create new partitions and choose the filesystem to Write any file with any size to read and write anywhere* in the plug and play fashion for both HDs. Something just like this only one partition:

/dev/sdb1            500000000     0    500000000  0% /media/My Passport

I had handled virtual filesystems before, but I would like to solve that quickly because I dont have time to get from my MSc studies.

Somebody could help me and possible other people that bought that external HD?

Thanks in advance. :)

* I can't install anything in the windows machine at the office

---


---
title: "want windows back a.s.a.p"
date: 2007-11-11
forum: Desktop Environments
---

### Post by finlandrocks on 2007-11-11
ok first off sorry if this is a repost! i want & need windows back asap, i run a mesh laptop and cant get windows to install as it doesnt recognise theres even a HDD on my laptop! 
all i want is my laptop back to normal, i love ubuntu but........no wifi/blutooth or even midi (im a musician)

how do i go about it in non-geek layman terms, i need to install XP pro, create an NTFS partition etc, etc

Please help!! 

simon

---

### Post by oilchangeguy on 2007-11-11
does the computer have a floppy drive? head over to [www.bootdisk.com](www.bootdisk.com) and create a 98 boot floppy. i think you can also burn a cd as well. but using the floppy/cd boot the computer from it. and at the a:> type fdisk. and follow the prompts to delete the non logical partition. then create a new partiton. then your windows cd should work.

---

### Post by finlandrocks on 2007-11-11
hi oilchang guy, thanks for getting back to us, main prob im having is xp pro simply wont recognise the HDD even existing, even when i have created a NTFS/FAT file system partition.

when im installing xp pro, it goes fine until the copy files section crops up,informs me theres no HDD to install on! grrrr. its a fujitsu HDD if this is any help. last resort maybe a live CD xp pro, but how do i do that?

any help is appreciated! .

---

### Post by FIONEX on 2007-11-11
First things first:  Wifi, bluetooth, and midi are now standard in xubuntu.  So download a fresh ISO from xubuntu.org and just try booting off the cdrom and it should work.

Anyways, if you had windows before and it cant recognize the drive now then you might wanna repartition from scratch (lose all the data) or then your bios doesn't have the right settings for the hard drive.  Some BIOS firmwares have an option to select what type of OS will be on the disk, and that may help.  You need a PRIMARY NTFS or FAT partition for windows to be able to install.

---

### Post by bigken on 2007-11-11
have you tried the gparted liveCD to reformat your hdd ?

---

### Post by djgenesis on 2007-11-11
> **finlandrocks said:**
> ok first off sorry if this is a repost! i want & need windows back asap, i run a mesh laptop and cant get windows to install as it doesnt recognise theres even a HDD on my laptop! 
all i want is my laptop back to normal, i love ubuntu but........no wifi/blutooth or even midi (im a musician)

how do i go about it in non-geek layman terms, i need to install XP pro, create an NTFS partition etc, etc

Please help!! 

simon


Find "hirens boot CD" and use "Partition Magic£. 
That'll do the trick ;)
Hope it helps
xxGenxx

---

### Post by bigken on 2007-11-11
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

---

### Post by finlandrocks on 2007-11-12
hi, thanks everyone for all your help as it does seem to look like i dont like ubuntu, not the case if your wondering, i have a second laptop that i will rehome ubuntu on, but my primary baby needs xp lol.

downloaded roadstarter hirens live cd, by the looks of its contents i should get ol' xp back in no time. i shall let you all know on the success.

any future plan for ubuntu to be on  NTFS? this really would make things easier for newbies, as if it doesnt work out getting ol' windows back would be a doodle!

so what i have to do is re-partition from within the live cd ? do i need to re-format too?

cheers,simon

---

### Post by zaphod777 on 2007-11-12
if it doesnt show your hdd it probably has a SATA HDD you need to download the driver put it on a floppy and hit F6 or whatever when prompted to install third party drivers when botting the XP disk. 

I would say that there is no plan to put NTFS into linux it is  a patented file system that microsoft owns and it is not open source. Just getting write support has been difficult.

---


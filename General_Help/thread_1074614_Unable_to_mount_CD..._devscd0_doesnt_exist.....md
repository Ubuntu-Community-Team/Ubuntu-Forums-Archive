---
title: "Unable to mount CD... /dev/scd0 doesnt exist...."
date: 2009-02-19
forum: General Help
---

### Post by mjrodriguez on 2009-02-19
This is my first posts. Thx in advanced to the Ubuntu Community, i think u are doing an amazing job...

Here is the problem:

I had Ubuntu 8.04 working perfectly
 then i upgraded to 8.10. I didnt noticed and i dont know if this had any influence, but my CDRW drive was not connected. A few weeks ago, i reconnected it and noticed that it didnt mount on the startup. So i checked the /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5cc0979e-e880-466a-87f9-e34a62a249ec /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sda5
 UUID=1903f2b7-4320-49b1-9c99-a9a8d0c22d97 none            swap    sw              0       0
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Apparently this is correct, but when i try to do it manually there is a message that says "/dev/scd0 device doesnt exist" (my ubuntu is in spanish so this message aint literal)

The main problem is... /dev/scd0 doesnt exists. Neither does /dev/scd1 or any other device different than my hard disks (/dev/sda, /dev/sda1, etc)

I also looked for /dev/hd* but there no files were found...

So... im out of options... Is there anyway to install it or something?

Thx again. I'll wait for ur answer and please, excuse my english, it aint as good as it used to be...

---

### Post by heindsight on 2009-02-19
Well, my first suggestion would be to make sure that your drive is indeed properly connected, maybe try disconnecting and reconnecting it again.

Try running 
```
sudo lshw -C disk
``` to see if your drive is detected at all.

---

### Post by mjrodriguez on 2009-02-20
> **heindsight said:**
> Well, my first suggestion would be to make sure that your drive is indeed properly connected, maybe try disconnecting and reconnecting it again.

Try running 
```
sudo lshw -C disk
``` to see if your drive is detected at all.

Ty very much for ur answer. After trying it i got this:
  *-disk:0                
       description: ATA Disk
       product: ST320413A
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.40
       serial: 6ED3XRD2
       size: 18GiB (20GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=c8277fb6
  *-disk:1
       description: ATA Disk
       product: WDC WD400EB-75CP
       vendor: Western Digital
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 06.0
       serial: WD-WMAATF309971
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=67452301

(lame disks indeed =P ) but no CDROM was found. Nevertheless the BIOS detects it and in case that was not enough, i can boot from it with my Ubuntu CD.
In few words, Ive got a CDRW that i know its working, but somehow, Ubuntu has no idea of it. 






PS: Ubuntu is still by far, the best OS available out there if you ask me

---

### Post by heindsight on 2009-02-20
That is strange, maybe there's some bug that prevents the drive from being recognized. Although if it worked in 8.04 i'd expect it to work in 8.10 too.

Perhaps try looking through the kernel boot messages to see if there's some indication there of what's going wrong. Do
```
less /var/log/dmesg
``` and search for CD (in case you don't know, to search in less press / and then enter the search string, use n to find the next occurrence and N to go back to the previous occurrence).

Another thing you could try is to manually load the kernel modules by doing
```
sudo modprobe -v sr_mod
```
I'm not sure that will make any difference, but it's worth a try. Hopefully it will at least give you an informative error message...

---

### Post by mjrodriguez on 2009-02-20
For the first time i saw something about my CDRW!
So its out there after all... 
Thanks very much for ur answer, these are the results:

(im just going to post the lines where the string "CD" was found)

.
.
.
[    4.829613] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xdc00 irq 14
[    4.829620] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xdc08 irq 15
[    5.000699] ata1.00: native sectors (39102335) is smaller than sectors (39102336)
[    5.000710] ata1.00: ATA-5: ST320413A, 3.40, max UDMA/100
[    5.000715] ata1.00: 39102336 sectors, multi 16: LBA 
[    5.001904] ata1.01: ATA-5: WDC WD400EB-75CPF0, 06.04G06, max UDMA/100
[    5.001911] ata1.01: 78165360 sectors, multi 16: LBA 
[    5.016574] ata1.00: configured for UDMA/100
[    5.034089] ata1.01: configured for UDMA/100
[    5.212470] ata2.00: ATAPI: LITE-ON CD-RW SOHR-5239V, 2$09, max UDMA/33
[    5.244382] ata2.00: configured for UDMA/33
[    5.244641] scsi 0:0:0:0: Direct-Access     ATA      ST320413A        3.40 PQ: 0 ANSI: 5
[    5.245014] scsi 0:0:1:0: Direct-Access     ATA      WDC WD400EB-75CP 06.0 PQ: 0 ANSI: 5
[    5.246317] scsi 1:0:0:0: CD-ROM            LITE-ON  CD-RW SOHR-5239V 2$09 PQ: 0 ANSI: 5
.
.
.
[    5.941994]  sdb: sdb1
[    5.984819] sd 0:0:1:0: [sdb] Attached SCSI disk
[    5.994832] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    5.994843] Uniform CD-ROM driver Revision: 3.20
[    5.995053] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.934285] PM: Starting manual resume from disk
[    6.934295] PM: Resume from partition 8:5
.
.
.
[   24.560288] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   24.560297] ata2.00: ATAPI check failed (ireason=0x2 bytes=0)
[   24.560308] ata2.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 16420 in
[   24.560310]          cdb 12 00 00 00 24 00 00 00  00 00 00 00 00 00 00 00
[   24.560312]          res 58/00:02:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
[   24.560317] ata2.00: status: { DRDY DRQ }
[   24.560350] ata2: soft resetting link
[   24.807552] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   24.807710] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   28.032459] ata2.00: model number mismatch 'LITE-ON CD-RW SOHR-5239V' != '^LI^TE-O^N ^CD-R^W ^SR-5239V'
[   28.032467] ata2.00: revalidation failed (errno=-19)
[   29.716059] ata2: soft resetting link
[   29.896405] ata2.00: model number mismatch 'LITE-ON CD-RW SOHR-5239V' != '^LI^TE-O^N ^CD-R^W ^SR-5239V'
[   29.896413] ata2.00: revalidation failed (errno=-19)
[   29.896420] ata2.00: disabled
[   34.872060] ata2: soft resetting link
[   35.028131] ata2: EH complete
[   35.028155] ata2.00: detaching (SCSI 1:0:0:0)
[   35.033335] scsi 1:0:0:0: rejecting I/O to dead device
[   35.033375] scsi 1:0:0:0: rejecting I/O to dead device
[   35.033398] scsi 1:0:0:0: rejecting I/O to dead device
[   35.994394] lp0: using parport0 (interrupt-driven).
.
.
.
And thats pretty much it... At least the CDRW is out there. But i really have no idea whats the next step from now on. 

Thx again for ur help.

---

### Post by heindsight on 2009-02-21
That dmesg output smells of hardware failure to me. You say you have no problem booting from the CD drive though, so maybe there's some other cause. Just to clarify, is the CD you're booting from an 8.04 CD or an 8.10 CD? If it's an 8.04 CD, then it may be that there's some crucial difference between 8.04 and 8.10 that stops the newer ubuntu working with your CDRW.

> [ 6.934285] PM: Starting manual resume from disk
[ 6.934295] PM: Resume from partition 8:5

It would seem the dmesg output you posted is from the machine waking from hibernation, rather than a full reboot. Have you tried completely rebooting, rather than just hibernating since reconnecting the CDRW?

---

### Post by nbarros on 2009-04-27
I was having the exact same problem, it started out of nowhere. Inside XP the drive worked fine, but the errcod -19 persisted before the ubuntu splash screen. I've disconnected the drive (it's an internal Toshiba ATA DVD burner), connected it back, and nothing changed. I have a spare LG DVD burner, connected it, and it just worked. After that, I connected the Toshiba back, and guess what... Yes, it worked.
The only thing that may have affected the system somehow, is that I am pretty sure the tray was open during the system startup at the first time the problem appeared. All the other situations the tray was closed.

God knows...

---


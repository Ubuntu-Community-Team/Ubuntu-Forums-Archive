---
title: "DVD drive cannot mount anything"
date: 2010-08-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bogustrumper on 2010-08-18
Hello,

Wasn't entirely sure which forum to place this, so mods if it needs to be moved I apologize.

I'm running a Dell Precision 690, and have Ubuntu 10.04 amd64 installed (completely fresh install).  The computer has two optical drives, a CD-ROM and a DVD+-RW drive.  I burned the Ubuntu install CD using the DVD+-RW drive in Windows, and installed using the CD-ROM drive.

Now, in Ubuntu, I can mount the CD just fine in the CD-ROM drive.  And mounting USB and what-have-you works just dandy; all icons show up on the desktop as I expect.  But if I put anything in the DVD drive, I get no response at all. Once in awhile I get the following error message:
```
Error mounting: mount: block device /dev/sr1 is write-protected, mounting read-only
mount: /dev/sr1 already mounted or /media/Ubuntu 10.04 LTS amd64 busy
```

Other machines have no problems with all of the DVDs I put in. I can even mount a CD just fine in the CD drive, then pop it in the DVD drive and nothing.

Trying to mount on the commandline does not get me any further; the command either hangs for awhile or I get a "device not found" error.

I've tried all the tricks I can find for similar-sounding problems: changing the boot order in the BIOS, changing the drive settings in BIOS from AHCI to ATA mode, disabling floppy disks in BIOS... even tried swapping the drive order, same behavior.

The drive shows up in "Disk Manager" as an HL-DT-ST DVD+-RW GWA4164B, running firmware D108.

Anybody have any other tips/tricks/ideas?  Frustrating, as I need to install some software that comes on a DVD.  My only workaround for now is to copy the DVD to an iso on another machine and transfer it over the network... which is fine to do once, but...

Here's the output of dmesg, from putting the Ubuntu install disk in the CD-ROM, mounting it, immediately ejecting and putting it into the DVD drive:

```
~$ dmesg | tail -21
[   64.778819] ISO 9660 Extensions: Microsoft Joliet Level 3
[   64.800839] ISO 9660 Extensions: RRIP_1991A
[  152.040068] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  152.040076] sr 0:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[  152.040093] ata1.01: cmd a0/01:00:00:00:10/00:00:00:00:00/b0 tag 0 dma 4096 in
[  152.040094]          res 40/00:02:00:0c:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  152.040098] ata1.01: status: { DRDY }
[  152.960025] ata1: soft resetting link
[  153.170226] ata1.00: configured for UDMA/33
[  153.220305] ata1.01: configured for UDMA/33
[  153.221900] ata1: EH complete
[  157.777196] ata1: drained 1024 bytes to clear DRQ.
[  157.777207] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  157.777213] sr 0:0:1:0: [sr1] CDB: Volume set (in), Read cd: be 00 ff ff ff ff 00 00 01 10 00 00
[  157.777231] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[  157.777232]          res 58/00:02:00:00:08/00:00:00:00:00/b0 Emask 0x2 (HSM violation)
[  157.777236] ata1.01: status: { DRDY DRQ }
[  157.831284] ata1: soft resetting link
[  158.051480] ata1.00: configured for UDMA/33
[  158.091580] ata1.01: configured for UDMA/33
[  158.093816] ata1: EH complete

```

---

### Post by olamina on 2010-12-19
im having the similar depressing problem, and just when i was hoping to burn some christmas CDs.  when i insert a dvd or CD the drive works fine, but it doesn't want to burn. 

when i enter

```
sudo mount /dev/sr0 /media/cdrom5
```

i get 

```

mount: block device /dev/sr0 is write-protected, mounting read-only

```

:( did you ever find a solution?

---

### Post by olamina on 2010-12-19
OK, never mind. I was putting in non-writeable disks. As soon as I stuck in an actually empty disk, everything worked smoothly. 

 "*Hello, IT, have you tried turning it off and on again?*" - Roy Trenneman, The IT Crowd

---


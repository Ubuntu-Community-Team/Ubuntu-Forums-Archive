---
title: "Drdy_error"
date: 2009-07-23
forum: Desktop Environments
---

### Post by TheNTW on 2009-07-23
I am having troubles with booting up my desktop. 
Now I have no idea what is going on, but my PC is falling apart. 

1. When power on, I have to reboot for like 10 times (until the lucky time...) to GRUB to load, or else I will get a blank screen with a _ blinking...

2. My CDrom Works. Only trouble is - when Ubuntu is loaded - it doesn't seem to work anymore (it did work sometimes a while ago, but now simply doesn't). I tried ejecting it all the time while Ubuntu was loading, but at one point ubuntu sucked the CD in and now won't give it back (can't do nothing about it). Ubuntu doesn't seem to understand that I have a CDrom.

Theese two issues are bugging me for a half a year already. I was patient, but well they have got worse by time, so Now I am posting a cry for help...

p.s. Maybe something from this will matter.

```
Jul 23 18:48:23 npc kernel: [   60.476910] ata3: EH complete
Jul 23 18:48:23 npc kernel: [   60.505464] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x400001 action 0x0
Jul 23 18:48:23 npc kernel: [   60.505467] ata3.01: SError: { RecovData Handshk }
Jul 23 18:48:23 npc kernel: [   60.505472] ata3.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 16396 in
Jul 23 18:48:23 npc kernel: [   60.505473]          cdb 43 00 00 00 00 00 01 00  0c 00 00 00 00 00 00 00
Jul 23 18:48:23 npc kernel: [   60.505474]          res 51/54:03:00:0c:00/00:00:00:00:00/b0 Emask 0x1 (device error)
Jul 23 18:48:23 npc kernel: [   60.505477] ata3.01: status: { DRDY ERR }
Jul 23 18:48:23 npc kernel: [   60.506458] ata3.01: limiting speed to PIO4
Jul 23 18:48:23 npc kernel: [   60.506461] ata3.01: exception Emask 0x10 SAct 0x0 SErr 0x400101 action 0x0
Jul 23 18:48:23 npc kernel: [   60.506464] ata3.01: SError: { RecovData UnrecovData Handshk }
Jul 23 18:48:23 npc kernel: [   60.506469] ata3.01: cmd a0/01:00:00:20:00/00:00:00:00:00/b0 tag 0 dma 16416 in
Jul 23 18:48:23 npc kernel: [   60.506470]          cdb 51 00 00 00 00 00 00 00  20 00 00 00 00 00 00 00
Jul 23 18:48:23 npc kernel: [   60.506471]          res 51/b4:03:00:00:00/00:00:00:00:00/b0 Emask 0x10 (ATA bus error)
Jul 23 18:48:23 npc kernel: [   60.506474] ata3.01: status: { DRDY ERR }
Jul 23 18:48:23 npc kernel: [   60.506479] ata3.00: hard resetting link
Jul 23 18:48:23 npc kernel: [   60.824008] ata3.01: hard resetting link
Jul 23 18:48:23 npc kernel: [   61.300051] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 23 18:48:23 npc kernel: [   61.300068] ata3.01: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jul 23 18:48:23 npc kernel: [   61.356185] ata3.01: configured for PIO4
Jul 23 18:48:23 npc kernel: [   61.356899] ata3: EH complete
Jul 23 18:48:23 npc kernel: [   61.369143] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x400001 action 0x0
Jul 23 18:48:23 npc kernel: [   61.369147] ata3.01: SError: { RecovData Handshk }
Jul 23 18:48:23 npc kernel: [   61.369152] ata3.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 16396 in
Jul 23 18:48:23 npc kernel: [   61.369153]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
Jul 23 18:48:23 npc kernel: [   61.369154]          res 51/54:03:00:0c:00/00:00:00:00:00/b0 Emask 0x1 (device error)
Jul 23 18:48:23 npc kernel: [   61.369157] ata3.01: status: { DRDY ERR }
Jul 23 18:48:23 npc kernel: [   61.369171] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
Jul 23 18:48:23 npc kernel: [   61.369180] sr: Sense Key : Aborted Command [current] [descriptor]
Jul 23 18:48:23 npc kernel: [   61.369184] sr: Add. Sense: No additional sense information
Jul 23 18:48:23 npc kernel: [   61.370063] ata3.01: limiting speed to PIO3
Jul 23 18:48:23 npc kernel: [   61.370067] ata3.01: exception Emask 0x10 SAct 0x0 SErr 0x400101 action 0x0
Jul 23 18:48:23 npc kernel: [   61.370069] ata3.01: SError: { RecovData UnrecovData Handshk }
Jul 23 18:48:23 npc kernel: [   61.370073] ata3.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jul 23 18:48:23 npc kernel: [   61.370073]          cdb 1e 00 00 00 01 00 00 00  00 00 00 00 00 00 00 00
Jul 23 18:48:23 npc kernel: [   61.370074]          res 51/b4:03:00:00:00/00:00:00:00:00/b0 Emask 0x10 (ATA bus error)
Jul 23 18:48:23 npc kernel: [   61.370076] ata3.01: status: { DRDY ERR }
Jul 23 18:48:23 npc kernel: [   61.370081] ata3.00: hard resetting link
Jul 23 18:48:23 npc kernel: [   61.688009] ata3.01: hard resetting link
Jul 23 18:48:23 npc kernel: [   62.164050] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 23 18:48:23 npc kernel: [   62.164067] ata3.01: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jul 23 18:48:23 npc kernel: [   62.220185] ata3.01: configured for PIO3
Jul 23 18:48:23 npc kernel: [   62.220895] ata3: EH complete
Jul 23 18:48:23 npc kernel: [   63.935120] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x400001 action 0x0
Jul 23 18:48:23 npc kernel: [   63.935124] ata3.01: SError: { RecovData Handshk }
Jul 23 18:48:23 npc kernel: [   63.935129] ata3.01: cmd a0/00:00:00:00:08/00:00:00:00:00/b0 tag 0 pio 2048 in
Jul 23 18:48:23 npc kernel: [   63.935130]          cdb 28 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00
Jul 23 18:48:23 npc kernel: [   63.935131]          res 51/54:03:00:00:08/00:00:00:00:00/b0 Emask 0x1 (device error)
Jul 23 18:48:23 npc kernel: [   63.935134] ata3.01: status: { DRDY ERR }
Jul 23 18:48:23 npc kernel: [   63.935141] sr 2:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 23 18:48:23 npc kernel: [   63.935144] sr 2:0:1:0: [sr0] Sense Key : Aborted Command [current] [descriptor]
Jul 23 18:48:23 npc kernel: [   63.935148] Descriptor sense data with sense descriptors (in hex):
Jul 23 18:48:23 npc kernel: [   63.935149]         72 0b 00 00 00 00 00 0e 09 0c 00 54 00 03 00 00 
Jul 23 18:48:23 npc kernel: [   63.935157]         00 00 00 08 b0 51 
Jul 23 18:48:23 npc kernel: [   63.935161] sr 2:0:1:0: [sr0] Add. Sense: No additional sense information
Jul 23 18:48:23 npc kernel: [   63.935169] end_request: I/O error, dev sr0, sector 0
Jul 23 18:48:23 npc kernel: [   63.935171] __ratelimit: 30 callbacks suppressed
Jul 23 18:48:23 npc kernel: [   63.935173] Buffer I/O error on device sr0, logical block 0
Jul 23 18:48:23 npc kernel: [   63.936200] ata3.01: exception Emask 0x10 SAct 0x0 SErr 0x400101 action 0x0
Jul 23 18:48:23 npc kernel: [   63.936203] ata3.01: SError: { RecovData UnrecovData Handshk }
Jul 23 18:48:23 npc kernel: [   63.936209] ata3.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jul 23 18:48:23 npc kernel: [   63.936209]          cdb 1e 00 00 00 01 00 00 00  00 00 00 00 00 00 00 00
Jul 23 18:48:23 npc kernel: [   63.936210]          res 51/b4:03:00:00:00/00:00:00:00:00/b0 Emask 0x10 (ATA bus error)
Jul 23 18:48:23 npc kernel: [   63.936213] ata3.01: status: { DRDY ERR }
Jul 23 18:48:23 npc kernel: [   63.936218] ata3.00: hard resetting link
Jul 23 18:48:23 npc kernel: [   64.252009] ata3.01: hard resetting link
Jul 23 18:48:23 npc kernel: [   64.728056] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 23 18:48:23 npc kernel: [   64.728066] ata3.01: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jul 23 18:48:23 npc kernel: [   64.784184] ata3.01: configured for PIO3
Jul 23 18:48:23 npc kernel: [   64.784699] ata3: EH complete
Jul 23 18:48:23 npc kernel: [   64.868154] ata3.01: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x0
Jul 23 18:48:23 npc kernel: [   64.868157] ata3.01: SError: { UnrecovData Handshk }
Jul 23 18:48:23 npc kernel: [   64.868162] ata3.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jul 23 18:48:23 npc kernel: [   64.868163]          cdb 1e 00 00 00 01 00 00 00  00 00 00 00 00 00 00 00
Jul 23 18:48:23 npc kernel: [   64.868164]          res 51/b4:03:00:00:00/00:00:00:00:00/b0 Emask 0x10 (ATA bus error)
Jul 23 18:48:23 npc kernel: [   64.868166] ata3.01: status: { DRDY ERR }
Jul 23 18:48:23 npc kernel: [   64.868172] ata3.00: hard resetting link
Jul 23 18:48:23 npc kernel: [   65.188009] ata3.01: hard resetting link
Jul 23 18:48:23 npc kernel: [   65.664050] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 23 18:48:23 npc kernel: [   65.664067] ata3.01: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jul 23 18:48:23 npc kernel: [   65.720184] ata3.01: configured for PIO3
Jul 23 18:48:23 npc kernel: [   65.720892] ata3: EH complete
Jul 23 18:48:23 npc kernel: [   65.723114] end_request: I/O error, dev sr0, sector 0
Jul 23 18:48:23 npc kernel: [   65.723117] Buffer I/O error on device sr0, logical block 0
Jul 23 18:48:23 npc kernel: [   65.754064] ata3.01: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x0
Jul 23 18:48:23 npc kernel: [   65.754068] ata3.01: SError: { UnrecovData Handshk }
Jul 23 18:48:23 npc kernel: [   65.754073] ata3.01: cmd a0/00:00:00:5c:01/00:00:00:00:00/b0 tag 0 pio 16732 in
Jul 23 18:48:23 npc kernel: [   65.754074]          cdb 46 01 00 00 00 00 00 01  5c 00 00 00 00 00 00 00
Jul 23 18:48:23 npc kernel: [   65.754075]          res 51/40:03:00:00:00/00:00:00:00:00/b0 Emask 0x10 (ATA bus error)
Jul 23 18:48:23 npc kernel: [   65.754078] ata3.01: status: { DRDY ERR }
Jul 23 18:48:23 npc kernel: [   65.754084] ata3.00: hard resetting link
Jul 23 18:48:23 npc kernel: [   66.072008] ata3.01: hard resetting link
Jul 23 18:48:23 npc kernel: [   66.548051] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 23 18:48:23 npc kernel: [   66.548067] ata3.01: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jul 23 18:48:23 npc kernel: [   66.604184] ata3.01: configured for PIO3
Jul 23 18:48:23 npc kernel: [   66.604898] ata3: EH complete
Jul 23 18:48:23 npc kernel: [   66.606200] ata3.01: limiting speed to PIO0
Jul 23 18:48:23 npc kernel: [   66.606204] ata3.01: exception Emask 0x10 SAct 0x0 SErr 0x400101 action 0x0
Jul 23 18:48:23 npc kernel: [   66.606207] ata3.01: SError: { RecovData UnrecovData Handshk }
Jul 23 18:48:23 npc kernel: [   66.606213] ata3.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 16396 in
Jul 23 18:48:23 npc kernel: [   66.606214]          cdb 43 00 00 00 00 00 01 00  0c 00 00 00 00 00 00 00
Jul 23 18:48:23 npc kernel: [   66.606214]          res 51/40:03:00:00:00/00:00:00:00:00/b0 Emask 0x10 (ATA bus error)
Jul 23 18:48:23 npc kernel: [   66.606217] ata3.01: status: { DRDY ERR }
```

---

### Post by TheNTW on 2009-07-26
bump?

---

### Post by synapsys on 2009-07-27
> **TheNTW said:**
> my PC is falling apart. 

I think that's your problem. How old is your computer?

---

### Post by TheNTW on 2009-07-29
About a year.

And this is my motherboard:
[IMG]http://hardwaretechreview.com/wp-content/uploads/asus-maximus-extreme-1.jpg[/IMG]
Seagate Barracuda Hard disks, Core2Qad (Q9300 ) processor, nVidia GeForce GX2 (1gb) video card.... doesn't seem to me that this should be my PC's fault.

---

### Post by asmoore82 on 2009-07-29
99.999999% of the time {DRDY ERR } is failing hardware, most likely a drive.

It is *possible* that it is bad/loose/dirty SATA cable, see the odds above.

---

### Post by doas777 on 2009-07-29
I'm doing a recovery of a dying hdd with bad blocks ( dd conv=noerror) as a slave, and I get 5 of those errors per second. definitely a hard disk IO/bus issue.

---

### Post by TheNTW on 2009-07-29
So what should I do ? Can I recover in some way or something ? Or should I buy a new hard disk ? I am pretty low on financial resources right now...

---

### Post by doas777 on 2009-07-30
> **TheNTW said:**
> So what should I do ? Can I recover in some way or something ? Or should I buy a new hard disk ? I am pretty low on financial resources right now...


well getting a new HDD is probably non-optional (if you want a computer that is). with luck you will be able to recover the files from the old one, but you would be daft to rely on that disk any further.

---

### Post by 23meg on 2009-07-31
> **TheNTW said:**
> So what should I do ? Can I recover in some way or something ? Or should I buy a new hard disk ? I am pretty low on financial resources right now...

Replace your HD cables. If you can't immediately do that, unplug and straighten the existing ones, and/or try swapping power and data cables with your CDROM drive. The bus errors can be caused by faulty cables, and (I'm not sure about this, but) the "device error"s on your log may be a second order consequence of the former.

---

### Post by doas777 on 2009-07-31
can you get any SMART reading off the drive?
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by synapsys on 2009-08-01
Seagate makes a program to check its hard disks. It's called seatools, and it's windows based, but you can also download a bootable iso from their website. If that doesn't work, it's also included in the ultimate boot cd, another bootable iso. I am a computer tech by day, and I use it all the time with great results. It will tell you immediately if your hard drive is bad. If it's bad, you can make use of your 5 year seagate warranty and get another one free.

---

### Post by lwhitmore on 2009-11-15
Well, I had a whole slew of errors associated with my hard drive .. DRDY errors .. CRC check errors .. invalidations.  My computer would only boot intermittently.  My filesystem started to break apart - reiserfs would complain continually.  In short - I was in deep ****.

I eventually got my computer to boot off a usb stick so I could run reiserfsck to try to solve some of the problems - but the intermittent DRDY error would still occur.  I imagined it must have been because my drive was packing up, and as the drive is virtually new, I just put it down to very bad luck.  The main problem was I couldn't even mount the drive to copy off the files that weren't included in my backup.

Then in a moment of clarity hit me.. maybe the cable is loose / or some dust has got where it shouldn't have.  BINGO!

I reseated the cable - blew away any dust (in case there was any) - and my PC's now running (touch wood).

The moral of the story - check your cable first.  And backup - now!  This kind of nightmare always occurs when you least expect it to.

---


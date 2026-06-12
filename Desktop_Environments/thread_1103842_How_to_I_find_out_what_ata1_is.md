---
title: "How to I find out what ata1 is ?"
date: 2009-03-23
forum: Desktop Environments
---

### Post by oygle on 2009-03-23
Have been seeing lots of [Hard drive errors]("http://ubuntuforums.org/showthread.php?t=1038608") , and would like to know how I can determine what device is ata1  ?

> Mar 23 19:26:38  kernel: [  697.052480] ata1.00: exception Emask 0x2 SAct 0x0 SErr 0x80400 action 0x6
Mar 23 19:26:38  kernel: [  697.052489] ata1.00: irq_stat 0x44000001
Mar 23 19:26:38  kernel: [  697.052496] ata1: SError: { Proto 10B8B }
Mar 23 19:26:38  kernel: [  697.052508] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Mar 23 19:26:38  kernel: [  697.052510]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Mar 23 19:26:38  kernel: [  697.052513]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
Mar 23 19:26:38  kernel: [  697.052520] ata1.00: status: { DRDY ERR }
Mar 23 19:26:38  kernel: [  697.052533] ata1: hard resetting link
Mar 23 19:26:38  kernel: [  697.372042] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 23 19:26:38  kernel: [  697.372836] ata1.00: configured for UDMA/66
Mar 23 19:26:38  kernel: [  697.372854] ata1: EH complete

---

### Post by oygle on 2009-03-24
Anyone know how to do this ? It's probably a simple command at terminal ??

Oygle

---

### Post by kpatz on 2009-03-24
ata1 is typically your first IDE or SATA interface.  **dmesg | grep ata1** should show you more info.

---

### Post by oygle on 2009-03-24
Okay, many thanks, I was able to see the info from **dmesg**. So, my DVD sata drive would be ata2.

---

### Post by oygle on 2009-03-29
It seems the ata assignment is different, that is, not constant.

Today

> 
Mar 30 13:51:44 kernel: [    3.716389] ata1.00: ATAPI: CRD-8483B, 1.02, max UDMA/33


which is the IDE interface, a CD-ROM.  Other days it might be one of the SATA interfaces.

Is there some CLI command to tell me which device has been assigned to each ata?  

If I do this ..

> 
# dmesg | grep ata1.
[    3.554356] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.716389] ata1.00: ATAPI: CRD-8483B, 1.02, max UDMA/33
[    3.724335] ata1.00: configured for UDMA/33
# dmesg | grep ata2.
[    3.554364] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.724390] ata2: port disabled. ignoring.
# dmesg | grep ata3.
[    3.725198] ata3: SATA max UDMA/133 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 19
[    3.880182] ata3.01: NODEV after polling detection
[    3.888226] ata3.00: ATAPI: ASUS    DRW-2014S1T, 1.00, max UDMA/66
[    3.904245] ata3.00: configured for UDMA/66
# dmesg | grep ata4.
[    3.725202] ata4: SATA max UDMA/133 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 19
[    4.180401] ata4.00: ATA-6: ST3200822AS, 3.01, max UDMA/133
[    4.180406] ata4.00: 390721968 sectors, multi 16: LBA48 
[    4.196426] ata4.00: configured for UDMA/133
# 


It tells me the info, but surely there is some CLI command, without having to wade through the system logs. The probem with using the system logs, is that it could be from the previous day (previous reboot).

---

### Post by oygle on 2009-04-01
Surely there is some CLI command, without having to wade through the system logs ?

---

### Post by thelamer on 2011-05-04
I am bringing this back from the dead. 

There has to be a way to determine this, the recommendation does not work if you have a whole bunch of the same devices plugged in (sofrtware raid) . They will all register as the same device in a seemingly random order. 

Emask errors or soft resets have been a guessing game. So far I have been unplugging the drives one by one to see what happens in the logs. This is not a great method.

There should be a log message like; 

[ 3.724335] ata1.00: registered as /dev/sda

Or something along those lines or some other way to link this up.

---


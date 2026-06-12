---
title: "softreset failed (device not ready) after updating to 9.04  today from 8.10"
date: 2009-04-23
forum: General Help
---

### Post by revelationman on 2009-04-23
I have updated to the latest release (which I am starting to regret) and now upon boot-up  I get softreset failed (device not ready) 

[    1.952018] ata1: softreset failed (device not ready)
[    1.952079] ata1: failed due to HW bug, retry pmp=0
[    2.116033] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.155945] ata1.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
[    2.155948] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.155963] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.214260] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.214263] ata1.00: configured for UDMA/133
[    2.548035] ata2: SATA link down (SStatus 0 SControl 300)
[    2.884035] ata3: SATA link down (SStatus 0 SControl 300)
[    3.220035] ata4: SATA link down (SStatus 0 SControl 300)

I am hoping there is solution to this I have filed a bug report and it seems there is many more getting this error. This is not a good sign for a new release with so much promise. Other then that once loaded all seems fine but again I am hoping there is a patch or a fix for this. 

:mad:

---

### Post by revelationman on 2009-04-24
I take it this could be from the new Kernel that was included in 9.04 well by the looks of it seems  this kernel is has some issue's 

Does anyone have a fix besides redoing the system or unfortunately going to another distribution. 

:confused:

---

### Post by Archmage on 2009-04-25
> **revelationman said:**
> Does anyone have a fix besides redoing the system

I don't think that redoing the system would do any good.

I'm getting this errors from a install on a blank hard drive and a 1 month old PC in 9.04:

```

[    1.266152] ata1: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff900 irq 2301
[    1.266155] ata2: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff980 irq 2301
[    1.266158] ata3: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa00 irq 2301
[    1.266162] ata4: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa80 irq 2301
[    1.748027] ata1: softreset failed (device not ready)
[    1.748067] ata1: failed due to HW bug, retry pmp=0
[    1.912038] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.918379] ata1.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
[    1.918382] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.924802] ata1.00: configured for UDMA/133
[    2.424028] ata2: softreset failed (device not ready)
[    2.424065] ata2: failed due to HW bug, retry pmp=0
[    2.588037] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.588764] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB01, max UDMA/100, ATAPI AN
[    2.589714] ata2.00: configured for UDMA/100

```

---

### Post by rbrcurtis on 2009-05-06
I did a full reinstall for other reasons, I got this error before and I still get it after.  but ubuntu does boot up ok so I guess we'll see if there is any other impact...

---

### Post by birddog165 on 2009-05-07
I get this error. For my setup I'm guessing that the softreset is referring to a command the OS sends to my USB hard drive for starting. I leave my external drive plugged into my power strip and then I manually press the power button on my computer to start up. I'm thinking that the OS tells the hard drive to reset, and it just for some reason fails. My only issue is that I have to unplug the drive and plug it back in to get the drive to be recognised. It's a bit annoying.

Anyways, that's my life story there. Kthx

---

### Post by Pitboss on 2009-05-07
> **rbrcurtis said:**
> I did a full reinstall for other reasons, I got this error before and I still get it after.  but ubuntu does boot up ok so I guess we'll see if there is any other impact...

Same situation here.

---

### Post by superubu on 2009-05-22
I m getting the same error when it s booting but after it everything works fine.....

update from 8.10 to 9.04
dv5 amd dual core 64

---


---
title: "Boot time flakiness - ata1.00 failed to read native max address (err-mask=0x4)"
date: 2009-07-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by stevecoh1 on 2009-07-05
This is a Dell Inspiron 530.  I've had it for two years.  It was originally a Windows machine.  (I didn't know at the time Dell would have sold it to me with Ubuntu.)   It now runs 8.04.  Previously (about 3 months ago, it ran 7.10.  More or less since Day 1, I've had the following problem (in both OS versions).

It doesn't always boot up.  I don't boot it that often so it isn't a big deal but it's really annoying when I do.  Sometimes it boots the first time.  Sometimes it doesn't.  Sometimes it takes 2 or 3 times, eventually it boots.

When it fails, the orange progress bar goes back and forth.  I learned today how to remove the quiet and splash parameters to see what is going on.

When it succeeds, dmesg looks like this:

When it works, dmesg has something like this:
[   28.155310] ata1: SATA max UDMA/133 cmd 0xf800 ctl 0xf700 bmdma 0xf400 irq 18
[   28.155312] ata2: SATA max UDMA/133 cmd 0xf600 ctl 0xf500 bmdma 0xf408 irq 18
[   28.358861] ata1.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133
[   28.358865] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   28.425357] ata1.00: configured for UDMA/133

 When it fails, I see the following scroll by:

ata1.00 failed to read native max address (err-mask=0x4)

I don't believe there is anything wrong with the hard drive.  the check routines never find anything to complain about.

I should also mention that I have another identical hard drive that I use from time to time to make backups of the system as when doing system upgrades.  It is not currently connected.  I don't honestly remember which was the original one.

Is there some boot-time parameter I can use to end the insanity?   Or some other way to solve this problem?

---

### Post by stevecoh1 on 2009-07-05
Actually found a working solution myself:

[http://ubuntuforums.org/archive/index.php/t-862456.html](http://ubuntuforums.org/archive/index.php/t-862456.html)

It works!

---


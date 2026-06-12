---
title: "could strange factory config cause my upgrade probem?"
date: 2009-01-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BertP on 2009-01-19
As I mentioned in some earlier messages, I am have problems in attempting multiple times to upgrade to 8.04

I am a noob but I have a wild guess at what the problem may be
Please read on and tell me if I am on the right track.  

-----
When booting, I get a series of the following messages initramfs messages,   repeating endlessly with the following patern

-------------------------------------

320.450198 ] ata2:00 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

[ 320.450198 ] ata2:00 cmd a0/00:00:00:24:00/00:00:00:00:00:/a0 tag 0 pio 36 in

[ 320.450198 ] ata2:00 status { DRDY }
------------------------------------------

So I checked my bios to see what was at ata2

but found that I didn't have one!


Here is a list my my SATA channels

SATA0  (harddrive modelb #s)
SATA1  (DVD +R +W model #s)
SATA2   GRAYED OUT
SATA3   GRAYED OUT
SATA4  (unassigned but present)
SATA5  (unassigned but present)

could it be that because I have 4 active SATA channels that Ubuntu is assuming that one of these will be SATA2 and therefore it spits out  error messages when it cannot contact SATA2?

If this is the problem, then how do I fix it?

---

### Post by superm1 on 2009-01-20
Try changing the ATA mode in the BIOS.

---


---
title: "How to image a compactflash card"
date: 2009-01-07
forum: General Help
---

### Post by Phayder92889 on 2009-01-07
I'm fixing a pair of Point-of-Sale machines built on a very dumbed-down PC architecture. They use compactflash cards as hard disks, and run win98. I have one with a failing CF card (64mb), one with a good CF card (32mb) but busted screen, and a blank CF card (128mb). I need to directly image over the good CF card to the blank CF card, maintaining /all/ settings, as it's an identical system in every way. There are no peripherals, nothing but a proprietary mobo and the hookups for power, ethernet, and serial.

I've used dd to create a verbatim image of the device onto my desktop, but it's too small for the 128mb card's purposes. I think this is possible, but I'm not sure how. gparted throws errors at me when I try and check the cards' integrity.

---

### Post by bc90021 on 2009-01-07
I was following along fine until that last paragraph... what's too small?  Do you mean that the 32mb or 64mb images are too small for the 12mb card?

Also, you should be able to store images of any of the CF cards onto your desktop in a file, with DD as you mentioned.

Assuming /dev/xyz is the flash card mounted in Ubuntu:

dd if=/dev/xyz of=/path/cf_card_32.dd

Then you can partition the 128mb card with only the size partition that you need - use cfdisk.  Sure, you'll be "wasting" part of the 12mb card, but that shouldn't be an issue.

Once you've partitioned the 128mb card to contain a 32mb or 64mb partition, simply use DD to copy it back:

dd if=/path/cf_card_32.dd of=/dev/abc

where /dev/abc is the 128mb card with a 32mb or 64mb partition.

If that's not what you meant, please clarify.

---

### Post by Phayder92889 on 2009-01-07
Yeah, that's what I meant, but will that work? Gparted tells me that the sizing and other such things are off, and that windows won't like it. I only really get one shot at this, and I'd like to not fsck it up...

It has to be bootable, and the card that I dd'ed over was working. Is there any chance that it's going to throw another error at me?

---


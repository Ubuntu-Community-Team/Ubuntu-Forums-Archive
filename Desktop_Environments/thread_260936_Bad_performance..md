---
title: "Bad performance."
date: 2006-09-19
forum: Desktop Environments
---

### Post by yuneyev on 2006-09-19
Hi everyone.

Not sure if this is the best forum to post this, but I'm with a little problem.

I recently installed Ubuntu on my pc, a 2.6 Celeron D, 760~MB, 40GB HD. All the rest is onboard stuff.

The problem is that Ubuntu is too slow here and I dunno why. Does it supposed to be with this computer?
It does all his tasks and stuff, but really slowly...sometimes even the music that I'm listening stops for a while.

Do you guys have any idea of what I could do to make it better?

Thanks =)

---

### Post by wkulecz on 2006-09-19
What video chip?  If Nvidia, there is a performance regression that makes the Xserver hog CPU if applications use the Xvideo extensions.

This may be gibberish to you, but if you have an Nvidia video card (or integrated chipset) try installing the proprietary "nvidia" driver.  Good howtos are on this forum.

If you some other video card, ignore this message.

--wally.

---

### Post by yuneyev on 2006-09-19
No...it's not Nvidia man, it's an onboard video chip.
You know...that one that is integrated with the motherboard.

Thanks anyway =)

---

### Post by wkulecz on 2006-09-19
It'd help a lot if you find out what integrated video chip your motherboard has.  

Nvidia is a common one, others major ones are ATI and Intel.  Recent ATI chipsets have been somewhat problematic with Linux.

Some of the integrated video chips are broken, so disabling in the BIOS and intalling an AGP or PCI-Express video is the only real fix.  If its one of those thankfully rare motherboards with integrated video and only PCI slots you're pretty much hosed.

--wally.

---


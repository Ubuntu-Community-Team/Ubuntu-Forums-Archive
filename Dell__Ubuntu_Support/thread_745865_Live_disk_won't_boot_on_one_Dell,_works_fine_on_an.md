---
title: "Live disk won't boot on one Dell, works fine on another Dell"
date: 2008-04-04
forum: Dell  Ubuntu Support
---

### Post by Mchl923 on 2008-04-04
I have Ubuntu7.1 on my 64 bit HP laptop, and I wanted to spread the love and made a 32 bit boot disk for my sisters laptop and our family desktop (both Dells).  The live disk works just fine on the laptop, but on the desktop I get the error :"strike f1 to retry boot, f2 for setup utility" and yes, it definitely is attempting to boot from the disk and yes the disk is definitely good (works fine on laptop).

---

### Post by niteshifter on 2008-04-05
Hi,

Optical drives vary. Optical media quality varies. Burn techniques vary. One data point does not a trend make.

Translation: There's nothing "definite" about the disk. 

Frequently folks burn at maximum speed as supported by the burner software and frequently the disks don't work. Try burning it at 4X and see if that works.

If that gets you nowhere, try the disk on as many other machines as you can. If it works on all of them, then you have a trend and a valid conclusion that the disk is OK - and the one failing machine has a faulty drive (dirty lens perhaps).

If it works on some, but not others then the burner machine or the media is at fault. Try a differenct machine for the burn or different (better quality) media.

---

### Post by Mchl923 on 2008-04-05
When I put the disk in while windows is running on the deesktop, a window opens that says se stuff about free windows software and that I can install Ubuntu by booting "from this disk."  does this not necessarily mean that the disk is good?

---

### Post by niteshifter on 2008-04-05
No. What that means is the the disk's TOC (content table), the file system table and some files (but not necessarily all files) can be read correctly. A bad spot can be anywhere on the disk.

For real, if you burnt the disk at max speed, do try a 4X burn. That's fixed the problem for many a user.

---


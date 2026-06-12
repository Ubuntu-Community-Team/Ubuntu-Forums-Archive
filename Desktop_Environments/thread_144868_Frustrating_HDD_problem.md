---
title: "Frustrating HDD problem"
date: 2006-03-15
forum: Desktop Environments
---

### Post by kc2idf on 2006-03-15
I have a very frustrating HDD problem that seems to be triggered by putting a particular motherboard together with any Debian derivitave.  As Ubuntu is my Debian derivative of choice, it is relevant here.

Other people have posted this problem to this forum and that, and, inevitably gotten a reply of "looks like a bad hard drive".  I believe this answer is incorrect, because of what I have tried.

I have:
Two Via Epia MII motherboards (identical in every way)
Two Seagate 250GB HDDs (Brand new), ATA/100
One Western Digital 120GB HDD (three years old) ATA/66
One Western Digital 10GB HDD (very old) ATA/33

I have tried:
Motherboard #1 with the 10GB drive with Ubuntu
Motherboard #1 with a 250GB drive with Ubuntu
Motherboard #1 with a 250GB drive with Slackware
Motherboard #2 with the 120GB drive with Fedora Core
Motherboard #2 with the 120GB drive with Ubuntu
Motherboard #2 with a 250GB drive with Ubuntu

In all cases involving Ubuntu, with these motherboards, I get sporadic issues with the hard drive freezing up for up to 30 seconds, and I get the following on the console:

hda: timeout waiting for DMA
hda: drive not ready for command
hda: no DRQ after issuing MULTWRITE_EXT

Note again, all three hard drives are PROVEN GOOD using non-Debian systems.  Both motherboards are PROVEN GOOD using non-Debian systems.  

I have also tried compiling a custom kernel, but the problem remains.  

So what "not the kernel", "not the HDD", "not the motherboard" thing is there that could cause this problem?

---


---
title: "I'm not being able to boot from cd drive"
date: 2009-06-06
forum: General Help
---

### Post by The Peabody on 2009-06-06
I'm trying to boot from a windows recovery disk for someone and I'm having issues, specifically the process seems to start but then cuts to normal booting and Ubuntu starts up. This is more or less what happens on screen:

"Loading RAMDISK image" (and a solid loading bar)

Something about Toshiba Recovery Disk (a segmented loading bar) (this only flashes for an instant, and is followed by a "Please Wait" loading bar that cuts to the Ubuntu splash after a short moment of black screen.

I know I'm supposed to be staring at that segmented loading bar for a long time, and the fact that I get to that point at all but can't complete the process worries me a lot.

Anyone know what's going on?

This is a Toshiba Satellite laptop, I had no problem using the boot from cd feature on this laptop or using the recovery disk on another laptop of the same series before.

---

### Post by markharding557 on 2009-06-06
this is ubuntu forum not windows you need a windows forum

---

### Post by The Peabody on 2009-06-07
oh... but i don't understand why they would help me with a ubuntu machine. that is all i have on this computer. it's not a windows problem if windows isn't on it. i believe ubuntu is somehow preventing the disk from being read.

---

### Post by Therion on 2009-06-07
Ubuntu isn't doing anything if you're trying to boot from a Windows CD; the BIOS directs the PC to boot from the optical drive if it detects bootable media in the drive at startup.

What exactly do you mean by "Windows Recovery Disk"?  Is it the factory Restore CD that came with that particular Toshiba laptop?  Those Factory Restore CD's are "tied" the machine they came with, you can't use any Factory Restore CD on any computer, even if from the same model line and/or made by the same manufacturer.  It don't work that way.

**EDIT:**  Having re-read your post a few times it sounds like you ARE trying to use a Restore CD from another laptop.  I suspect what's happening is this...  BIOS detects bootable media in the optical drive and attempts to boot from it.  There's a hash-mismatch between the hardware on the PC and the Restore CD.  Booting from the CD fails so the startup procedure continues on to the next bootable device in the boot-chain, that being the hard drive and where Ubuntu is loaded, so of course the PC attempts to start Ubuntu.

If you want this lappy running Windows methinks you are probably looking at doing a full blown reformat and reinstall (to do the job right) from a proper Windows install CD.

---


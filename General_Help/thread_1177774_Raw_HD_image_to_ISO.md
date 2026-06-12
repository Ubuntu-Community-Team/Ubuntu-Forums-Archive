---
title: "Raw HD image to ISO?"
date: 2009-06-03
forum: General Help
---

### Post by orbitaldecay on 2009-06-03
**Quick Background**:

I'm attempting to use VirtualBox to piece together a live CD.  I'd like to install an OS via VirtualBox, then convert the virtual drive to an iso.  So far, I am only able to convert the virtual drive to a raw HD image.

**The Big Question**:

Does anyone know of an easy way to take a raw HD image and convert it to an ISO 9660 format?  I can think of a few very difficult ways, but I'm sure there's something simpler.

It is *essential* that the boot sector remain intact, as far as I know mkisofs can't do this (correct me if I'm wrong).

---

### Post by pawnrocket on 2009-06-03
You should move it onto a cdfs then make an iso... Share it and burn it...

if all you want to be able to do is adjust the operating system you can just mount the installer iso; chroot into it; make your modifications and burn it. Not unlike what remastersys and reconstructor do.

---

### Post by orbitaldecay on 2009-06-03
> **pawnrocket said:**
> 
if all you want to be able to do is adjust the operating system you can just mount the installer iso; chroot into it; make your modifications and burn it. Not unlike what remastersys and reconstructor do.

This is a good idea.

After using my brain for 2 seconds I realized that my original idea was stupid.  Installing an OS to a hard drive, rewriting the filesystem, and then trying to boot it on a different medium ... will never, ever, ever work.  Don't bother trying.

But for the record the -hard-disk-boot flag for mkisofs will do the trick, as far as converting a raw hard drive image to a bootable iso.  Not that it'd be very useful.

---

### Post by pawnrocket on 2009-06-03
if you want a hand I have a couple hours a night to help for a couple weeks. Are you just remastering something? What options are you not getting from the other re-mixers?

---

### Post by orbitaldecay on 2009-06-03
> **pawnrocket said:**
> if you want a hand I have a couple hours a night to help for a couple weeks. Are you just remastering something? What options are you not getting from the other re-mixers?

Thank you for the offer, though I don't really have any specific goal in mind.  Just trying to learn a little more about iso and booting and other such nonsense :)

---

### Post by pawnrocket on 2009-06-03
I did find a how to in the ubuntu documentation on what you are looking for. Creating custom live cd's from the command line. I don't recall the link but it can be googled.

---


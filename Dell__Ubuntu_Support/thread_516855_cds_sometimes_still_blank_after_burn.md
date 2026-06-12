---
title: "cds sometimes still blank after burn"
date: 2007-08-03
forum: Dell  Ubuntu Support
---

### Post by tutwabee on 2007-08-03
I've been trying to burn audio CDs in Serpentine.  When I stick a blank CD in it is recognized properly and Serpentine writes the CD all the way through without reporting any errors and the drive spins the CD during the whole process.  After the CD is ejected if I stick it back in it is still recognized as blank.  If I look at the bottom of the disc it looks blank.

I stuck the supposedly still blank disc back in the drive and tried it again.  This time it is still recognized as blank but when I look at the bottom of the disc it looks like there is data written to it, but the data ring looks lighter than usual.

Is this a hardware problem or could this be a software problem?

---

### Post by ridgeland on 2007-08-08
I've never tried Serpentine.
But I've burned CDs and DVDs using K3B and Nautilus.
Maybe try them to be sure it's software, not hardware.
Also settings in /etc/fstab can make a drive (CD) read-only, or root user only.

---

### Post by cogumbreiro on 2007-08-13
> **tutwabee said:**
> 
Is this a hardware problem or could this be a software problem?

Serpentine uses the same "recording engine" that Nautilus uses (nautilus-cd-burner). If you have blank CDs with nautilus sometimes, then it can be related to hardware or to nautilus-cd-burner. If this only happens with serpentine then it could be a software problem. Serpentine has a known bug (fixed in the next version) that does not allow the same file being added twice; could that be the problem? The key idea here is knowing if it is reproducible.

---


---
title: "New Disk Size"
date: 2006-08-08
forum: Desktop Environments
---

### Post by lisantir5 on 2006-08-08
I installed a new WD (Western Digital) 320Gig (ultra ata/eide) drive using a rocket133 controller card with onboard bios (controller was used to get beyond the size limitations).  I jumpered the drive to be a single drive (without slaves).  Without partitioning or formatting the 'Ubuntu' System utility says I have 299Gig drive (\dev\hdg).  Since I am new to Linux I would like to know the following:

1. Is the size OK?
2. Can I partition about 1/2 the drive in ext3 and leave the other half for later (I might want to have another partition for MSWINDOWS).
3. The controller folks supply an open source driver in tar format, should I install this (they also have one for SUSE but not UBUNTU)?

I've checked the other posts but can't find one that addresses this exact situation (most complaints come after partitioning/formatting).

Any advice, directions, or recommendations will be much appriciated.  :-)

---

### Post by Ramses de Norre on 2006-08-08
> **lisantir5 said:**
> 
1. Is the size OK?
That's probably the 1000/1024 thingy..

> **lisantir5 said:**
> 2. Can I partition about 1/2 the drive in ext3 and leave the other half for later (I might want to have another partition for MSWINDOWS).
Of course.

> **lisantir5 said:**
> 3. The controller folks supply an open source driver in tar format, should I install this (they also have one for SUSE but not UBUNTU)?
If it doesn't work without the driver: yes. If it works without it the driver is probably allready included in ubuntu (pretty much change if it's open source).

---


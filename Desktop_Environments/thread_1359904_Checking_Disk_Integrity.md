---
title: "Checking Disk Integrity"
date: 2009-12-20
forum: Desktop Environments
---

### Post by Geffers on 2009-12-20
I want to install a new disk in my laptop and copy over some partition images so retain its original setup.

On XP's disk manager I have the option to quick format or normal, which takes for ages; I'm not sure how gparted does it, it is a lot quiicker than the XP full format but not as quick as the XP quick format so am not sure of the pros and cons of either.

As gparted can't create NTFS systems I need to use both XP's disk manager as well as gparted for my Linux stuff.

Can the disk integrity be checked after partition images have been copied, preferably via Ubuntu/Linux rather than XP

Geffers

---

### Post by SecretCode on 2009-12-20
If you are prepared to go to the command line, [MKNTFS](http://man.linux-ntfs.org/mkntfs.8.html) from ntfsprogs can make an NTFS volume. 

That project also offers [NTFSFIX](http://man.linux-ntfs.org/ntfsfix.8.html), but this says 
> ... fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.
So it looks like you can't do a full integrity check without booting Windows.

---

### Post by Geffers on 2009-12-21
> **SecretCode said:**
> If you are prepared to go to the command line, [MKNTFS](http://man.linux-ntfs.org/mkntfs.8.html) from ntfsprogs can make an NTFS volume. 

That project also offers [NTFSFIX](http://man.linux-ntfs.org/ntfsfix.8.html), but this says 

So it looks like you can't do a full integrity check without booting Windows.

Thanks for reply, I did a full format on one drive which will hold the main XP partition and the others I did a quick format on the others.

The Linux partition will take care of itself.

Geffers

---

### Post by magniking1 on 2009-12-26
Given that your MacBook was asleep, it is a fair bet that the read/write heads of the drive were parked and would not have damaged your hard disk drive in the way that can happen if the drive were actively being written to at the time of the incident. Most drive manufacturers do have utilities that can check hard drive health, but very few of them (if any) run under OS X. TechTools Pro might be able to give some information, but if you just do a check of the file system using Disk Utility you should be able to see if there's any significant damage. If it comes back clean, or with errors it can repair, then you are probably in the clear.
=======================================================
[CJ Prestman Reviews](http://www.youtube.com/watch?v=2ZKz9ckh8Ag)
[Tyre Pressure Monitoring Systems, Car's, 4WD, SUV's and Trailers](http://www.tyrepitstop.com.au/tyre-pressure-monitoring.asp)

---


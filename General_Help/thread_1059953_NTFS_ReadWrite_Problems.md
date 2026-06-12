---
title: "NTFS Read/Write Problems"
date: 2009-02-04
forum: General Help
---

### Post by OneRingShort on 2009-02-04
I stumbled upon a problem with NTFS that I have never heard of before, and personally, it confuses the living crap out of me.

I have Windows Vista Ultimate and Ubuntu 8.10 installed on a single 500gb hard drive, with a terabyte drive as the /home.  I have two 320 other 320s as well.  I have been trying to share data between the two operating systems, and that is where I run into problems.  Previously, I would just install Ext2IFS on Windows, and be done with it, however, that doesn't seem to work anymore.  It recognizes the Ext3 drives, maps them, but you cannot access them (asks you to format them).

I figured since Windows didn't want to play fair, I would just format the two 320s as NTFS, so Windows could read them, and Ubuntu would have no problem read/writing on them.  I did the format, and copied all the data onto the NTFS through Ubuntu (the data was on an Ext3).  After several hours, the data is no the NTFS drive and can be read without a problem.  When I boot into Windows however, it shows that it is filled with the data, but when I open the drive, it says it's blank (See attached: the drive in question is Perseus).  I have checked, and they are not just hidden either.

If I reboot back into Ubuntu and check the drive again, it's no longer there.  The only thing present is $RECYCLE.BIN and System Volume Information.  It still says only 122gb are free though.

Any idea why Windows can't see any data that Ubuntu writes to NTFS?

---


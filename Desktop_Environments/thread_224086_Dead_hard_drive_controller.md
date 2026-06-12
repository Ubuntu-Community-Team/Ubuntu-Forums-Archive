---
title: "Dead hard drive controller?"
date: 2006-07-27
forum: Desktop Environments
---

### Post by boyfromthedwarf9 on 2006-07-27
I have a Gateway Tablet (Convertable), it originally had a 40gig drive.  I then upgraded it to an 80gig from my dad's old laptop.  This was working fine, without any problems until a few days ago.  The I first noticed a problem with the startup sound, it sounded like there was a deep tone behind it.  

Then the drive went to "Error 29" no write access, or something close.  I bought a new 120gig hard drive, and installed it myself (there is a easy drive access thing on the side).  

I reinstalled XP and Dapper, and they were working fine (I did have AIGLX problems but that isn't the drive's fault).  Just a few hours ago, I got the deep tone back in the startup sound.

I ran SpinRite 6, and I get Division Overflow Error at the same point (5672 if it matters), but only while checking the linux partitions.  HDA1 is XP, then HDA2-5 is Dapper (boot, root, extended, swap), and HDA6 is a fat32 for sharing between XP and Dapper.  I can scan HDA6 and HDA1, but HDA2-5 give me that error.

I'd appreciate any advice or help, I need a working laptop for school at the end of August.

---

### Post by boyfromthedwarf9 on 2006-07-27
Update:  After some digging around, I found out that the maximum that my Tablet (a Gateway M275 2ghz) can hold is an 80gig.  However, it did pickup my 120gig, and it has been working.  Although it says "Maximum Supported", the 80gig was a working pull (as far as I can tell), and when two drives have problems, I am hesitant to think it is two drives.

SpinRite did have the same problems on the 80gig I had in there before.

---


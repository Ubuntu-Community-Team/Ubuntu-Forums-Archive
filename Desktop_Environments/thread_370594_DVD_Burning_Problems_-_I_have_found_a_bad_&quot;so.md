---
title: "DVD Burning Problems - I have found a bad &quot;solution&quot;"
date: 2007-02-25
forum: Desktop Environments
---

### Post by Gallardo Spyder on 2007-02-25
For all those that may have a problem burning DVD's....

After several months now with Ubuntu 6.10 - and a long time Linux User (of multiple flavors).

I have had the normal issues - but the one which has plagued me the longest is getting my DVD burner to actually burn disks.

After countless coasters floating about my office (I was up to around 100 wasted disks).

I think I have found a "solution" - it is not a good one - but it has worked now several times - without fail.

________________

So to start - I am using Ubuntu 6.10 on this particular machine.  I have a Buslink external USB 2.0 CDRW/DVDRW drive.  The supported formats for the DVD burning are DVD +R, DVD RAM, and DVD +RW.  With a DVD Write Speed of 8x.

I had a few different brands of DVD on hand (to start) that I had used with Windoze XP - without fail for the last few years.  This machine used to be XP.  So after installation of Ubuntu 6.10 (no dual boot) clean installation.  DVD burning was failing with an Input/Output error - using either K3b or GnomeBaker.  (K3b would get a little further about 5% before failing.

Having read the multiple threads and problems that others were having with various brands of DVD burners (internal and external) - I tried all the threads inputs on potential soltions.  It should be noted that this drive would Burn CD's without an issue - just DVD's were the problem.

Having tried everything - over a period of months.  (this was the last thing I needed to work - so I could ensure I had backups of photos, etc).

I went through about 100 disks of all types and brands (each time I tried a fix/sugguestion - I tried to burn another one).

To make a very long story short - I went out this weekend and bought 12 different brands of various DVD +R and DVD +RW media.  Some got further in the burn process than the others - but only one worked...

Memorex DVD +R (16 X 4.7gb) disks.  

None of the DVD + RW will work at all (9 different types) - and none of the other DVD +R would complete without the I/O error.  

However it should be noted.  I have a few machines in my house.  Taking this USB DVD drive and hooking it up to my XP Laptop - worked and burned every single media that I tested on the 6.10 box - none failed...  So the media is supported for that drive outside of ubuntu...

It should also be noted that K3b will burn the Memorex I mentioned - GnomeBaker will NOT - it fails just like with the all the other media types in K3b and GnomeBaker).

The write speed in K3b (on all my disks regardless of media - is only about 1x (even if I select higher in K3b).  Which is painfully slow - But I have my backups working.

There needs to be a fix for this...  As this is not a real solution - and may just be luck that this one media type works for me.  (I have only burnt about 10 DVD's with it (averaging about 3GB each disk for my backups - but that seems pretty reasonable that after 10 disks it seems to be working).

It seems as if the growisofs is having a problem (or maybe the DVDrwtools) - I know there has been activity on this site - does anyone have any further information ?

Gspyder

---

### Post by tgalati4 on 2007-02-25
Sounds like you have made a strong case for keeping Windows around--to burn DVD backups!

---

### Post by Gallardo Spyder on 2007-02-26
> **tgalati4 said:**
> Sounds like you have made a strong case for keeping Windows around--to burn DVD backups!

Only reason I have any Windows machines is for work (company laptop and standards) otherwise I would not have any.

I am glad I got it "working" in ubuntu - but the solution is not a good one of course.

I am going to try it on my other distros - which I did not try.  I have Mepis 6.5 (beta), ubuntu Herd 4 (ff), Knoppix and, Mandriva on my other machines - I will give them a try as well to see if they work on them.  Each of those have internal CD writers - never a problem - but only my Home Network File Server (or my mainserver) has the need to have the DVD burner.

I have about 2 TB total disk hooked to the fileserver (ubuntu machine) - it is much easier to have the DVD burner hooked to this machine to do all my needed hard media backups - thus the passion to get this to a better workable solution.

Gspyder

---

### Post by tgalati4 on 2007-02-26
No doubt.  My experience with DVD is not good.  I recently replaced a lightly used HP LightScribe under warranty.  I wouldn't burn worth a crap even in Windows XP Pro.  HP replaced it after several hours of overseas technical support.  The drive was not worth the time I had to spend with tech support going through every conceivable scenario.  I have Dapper on that machine also, but I have only used it to burn CD's using K3B.  That has worked well so far.  I will try to burn some DVD's to see what works.

I did find a Linux LightScribe app, but I haven't played with that either.  A sharpie is so much quicker.

Good luck.

---


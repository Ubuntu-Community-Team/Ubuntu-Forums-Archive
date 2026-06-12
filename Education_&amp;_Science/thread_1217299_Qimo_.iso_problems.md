---
title: "Qimo .iso problems"
date: 2009-07-19
forum: Education &amp; Science
---

### Post by Bartender on 2009-07-19
Good day!
First things first.  I'm hobbled with dial-up at home, so I go to the library for broadband, then back home to try stuff out.  That should help to explain the SOE below.  It's not as simple as "just try downloading again."  Especially with the library closed the next two days!

I've successfully downloaded/burned at least 40 .iso's over the past couple of years.  On July 18 I downloaded Qimo 1.0 using Transmission.  The md5 checksum from the Qimo website matched.  I burned the .iso on our Ubuntu laptop using Brasero.  Re-booted, hit "Check CD for Errors", errors found in one file.  

I'm not sure if I've ever had a bad burn.  Maybe a few years ago. 

I took the CD to the test PC and booted.  The test PC also reported errors in one file, but I installed anyway.  Everything seemed OK.  On reboot I got a Qimo splash screen, but at the last minute the PC dumped to a standard Xubuntu desktop and there was an error message from Package Manager in the upper panel.

So I burned again, this time using a Windows PC and Sony NTI at 8X.  I've _never_ burned a bad install CD with this method.  The exact same thing happened - errors in one file.

This is the first time I've used a torrent instead of a mirror.  But the md5 matched.  And I used two different PC's to make two different CD's.  Both CD's are showing similar errors.

Anyone tried downloading Qimo recently and had any problems?

---

### Post by Bartender on 2009-07-19
I got a nice email from Michael Hall, the guy who's developing Qimo.

A CD built from the Qimo download always reports an error in one file if you run "Check CD for Errors".  It's not a show stopper.  Just proceed.

When installing, don't tick the "Log me in automatically" checkbox at the conclusion of the partitioning section.  If you do, the PC will insist on logging into the Xubuntu desktop.  Leave the checkbox alone and Qimo will come up by default as it's designed to do.  

As to the Package Manager error, just go online and get updates.  The error message goes away.

Problems solved.  Now if I could just get Tux Math to come up in a bigger window...

---


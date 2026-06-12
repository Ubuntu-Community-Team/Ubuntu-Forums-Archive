---
title: "Unable to Mount"
date: 2009-03-03
forum: General Help
---

### Post by .Cameron. on 2009-03-03
I was recently defragmenting one my secondary HDD on Windows using PerfectDisk 10. After a few hours, it prematurely ended the operation claiming it was done, after which Windows was in an unstable state. After much trial and error, I've come to the conclusion that the drive is, to some degree, corrupted (based on DOS tools). Windows (XP, Vista, 7) will all slow down immensely (30 Minutes just to boot) and all programs, including explorer are essentially unresponsive (even in safe mode) whenever the drive is connected.

I was hoping that I might be able to get something off of the drive with Ubuntu (if anything is even intact). I've tried forcing it to mount as an administrator and received two mounting errors:

[IMG]http://img25.imageshack.us/img25/903/56616244dm5.png[/IMG]

[IMG]http://img25.imageshack.us/img25/9043/60035164kj2.png[/IMG]

At one point, however, I somehow got the folder I was attempting to mount it on to appear in [FONT="Courier New"]/media/[/FONT]. I opened the properties window, and most details were "unreadable". When I tried to open the folder, I got yet another error:

[IMG]http://i211.photobucket.com/albums/bb147/Cameron_1337/Security.png[/IMG]

I've ran [FONT="Courier New"]CHKDSK [/FONT]in Windows as recommended several times; it would always find errors in the security descriptor (or something like that, don't specifically remember) and be unable to fix it. The drive is 320GB, formatted as NTFS, and only has one file I'm concerned about on it: a ~200GB+ PGP Disk file which is used to mount as a virtual drive. Is the data likely recoverable, and if so, how would I go about retrieving it?

---


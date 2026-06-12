---
title: "Samsung ML-2510 on 6.06"
date: 2006-10-11
forum: Desktop Environments
---

### Post by boca raton on 2006-10-11
Purchased a Samsung ML-2510 laser printer as it is 'Linux friendly'.  I've not been able to find enough info to get thru installation tho.  I have the cd it came with, when I try it, it flashes a terminal window and stops (and some posts indicate it is not useful anyway).

Downloaded the OEM UnifiedLinuxDriver and tried it.  It opens to terminal and 'falls apart' leaving a message to the effect 'root privlages are required to must be root to install driver package.  I've tried to do it with sudo with no success. I don't want to set any permanent root privlages which I can't reverse (inexperience showing here).

I've been using Linux for a year or more, I'm not the most apt user yet, this is frustrating.

I would like help to get this printer installed and running well. If I've missed some appropriate post then let me know.
(But be fairly simple in your recommendations)

Thanks in advance

---

### Post by Sef on 2006-10-11
> I've tried to do it with sudo with no success.

Have you tried using gksudo?  That sets up a temporary root situation.

---

### Post by boca raton on 2006-10-12
Yep, it worked!  Didn't know I could gksudo nautilus.

From terminal used gksudo nautilus and ran the Samsung installer.  Did have to change paper selection from A4 to letter, and failed to print a test page several times.  Putzed with it and finally rebooted the PC and the printer worked!

Thanks again!

---


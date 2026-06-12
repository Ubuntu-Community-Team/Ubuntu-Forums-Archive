---
title: "jPilot won't run on new install of Dapper Drake"
date: 2006-07-28
forum: Desktop Environments
---

### Post by imafishimafish on 2006-07-28
Hi, I just installed 6.06 last week, and I'm trying to get away from Windows completely.
 Part of this is being able to use my Palm Pilot in Ubuntu.
 I read that jPilot is good (some say better than Palm Desktop for Windows).
 So I installed jPilot (0.99.8-0.99.9-pre2-1)
 and when I run, I get this error:

$ ./jpilot
*** glibc detected *** free(): invalid pointer: 0x081152a8 ***

Any ideas on how to make this work?

---

### Post by jonrkc on 2006-07-28
Sorry I can't solve this problem.  I installed Dapper the first week it was officially released, and JPilot on the same day, I'm sure, since I depend on it for my Palm use and have for three years since getting rid of that other operating system.  I just checked and I have the same version as yours.  I haven't had any problems--once I got the correct USB device specified under "Settings."

Have you tried "dpgk-reconfigure jpilot"?  Or perhaps "aptitude reinstall jpilot"?  That's the only two things I can think of that I'd try first if JPilot didn't work.  

Wish I could be more helpful.  Once you get JPilot going, I think you'll like it.  Meantime, you might try KPilot (the KDE application) and see if it presents the same or a similar problem.

---

### Post by Marc Higgins on 2006-07-30
I install jpilot, 6.06 with the automatix repos, once I had done this & tolf jpilot that the plam was on /dev/pilot (connected via usb / cradle) my treo600 was rocking.:D

---

### Post by jonrkc on 2006-07-30
> **Marc Higgins said:**
> I install jpilot, 6.06 with the automatix repos, once I had done this & tolf jpilot that the plam was on /dev/pilot (connected via usb / cradle) my treo600 was rocking.:D
Marc, I think I'll try reinstalling the way you did.  Mine (Tungsten E) works OK w/ JPilot, but it syncs much slower than under Hoary.  (I skipped Breezy.)

It took literally about two seconds or even less to sync under Hoary, and it's taking about a minute or longer at best, sometimes longer than that, under Dapper.  Something's got to be wrong with that.

Thanks for the tip.

---


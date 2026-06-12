---
title: "Question about booting - Inspiron 1501"
date: 2007-12-10
forum: Dell  Ubuntu Support
---

### Post by BoyanSemerdzhiev on 2007-12-10
Hello to all,

I had recently bought a Dell Inspiron 1501 (AMD Sempron X2 64bit) and ever since wanted to install Ubuntu on it. Tried first with Gutsy, and it seemed to run smooth except for the boot. It takes ages and at some time the boot screen disappears, instead showing some errors of the kind "ata1: softreset failed", etc. Booting process finishes in around 6 minutes.
I really don't want to get back to Windows, so any help would be appreciated. :(

Here is a copy of my system log, where you can see the output while booting:
```
12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.204000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)

12/10/2007 06:43:56 PM	inspiron	kernel	[   42.516000] ata1: soft resetting port

12/10/2007 06:43:56 PM	inspiron	kernel	[   43.020000] ata1: reset failed (errno=-5), retrying in 10 secs

12/10/2007 06:43:56 PM	inspiron	kernel	[   43.020000] ata1: softreset failed (1st FIS failed)
```
Thank you in advance!

---

### Post by Bronto on 2007-12-10
[http://www.ubuntu1501.com/2007/11/fix-for-gutst-taking-forever-to.html](http://www.ubuntu1501.com/2007/11/fix-for-gutst-taking-forever-to.html)

---

### Post by BoyanSemerdzhiev on 2007-12-10
Forgot to mention I have tried that, it didn't work. It just adjusted my boot screen resolution, so i can see the progress bar. Doesn't help at any case with the boot problem :(
Any other ideas?

---

### Post by BoyanSemerdzhiev on 2007-12-11
Pleaase, anyone with a similar problem, share the solution [-o<

---

### Post by jazzybob on 2007-12-11
Save your settings, etc., and do a clean install of gutsy.  or . .  email redDEAD, the author of the very cool ubuntu1501 blog referenced above.

With the exception of the NDISWRAPPER fix for the wireless in 7.04, his instructions are very good, easy to understand and implement.

---

### Post by redDEADresolve on 2007-12-11
you make sure you did the guide correctly? it should solve all your problems.

---


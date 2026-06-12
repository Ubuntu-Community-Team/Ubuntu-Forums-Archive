---
title: "Trouble with Startup"
date: 2006-08-28
forum: Desktop Environments
---

### Post by rrian on 2006-08-28
I'm not sure if this has already been asked, but I have a major problem with the starup of Ubuntu (6.06) on my machine.  When it's starting up, it stops at "Mounting root file system...", appears to be reding the CD, then says this error:

[17179699.400000] hdc: ide_intr: huh? expted NULL handler on exit
[17179718.684000] hdc: ide_intr: huh? expted NULL handler on exit
[17179718.732000] Buffer I/O error on device hdc, logical block 16312

Then the whole thing repeats over and over again, but with different accending numbers at the beginning (which I am assuming is date and time).

I have an Athlon 3400+ CPU and a 200 gb hard drive.  I've run a Scandisk to check the hard drive for errors, but I have no ideas on what to do to fix this problem.

Any help at all would be greatly appreciated.

Ian

---

### Post by mssever on 2006-08-28
I don't know what the problem is, but here are a few stabs in the dark...

Are you able to boot into recovery mode? Or into another OS? Can you mount and use the partition from the live CD?

---

### Post by rrian on 2006-08-28
I haven't tried recovery mode, but I do boot WinXP without problems.  I'm trying to only do the live CD mode, but I've also found I get the same error with Xubuntu and Edubuntu.  I've also tried it on other machines and not had any errors.  I'll try recovery mode and see what that does.

---


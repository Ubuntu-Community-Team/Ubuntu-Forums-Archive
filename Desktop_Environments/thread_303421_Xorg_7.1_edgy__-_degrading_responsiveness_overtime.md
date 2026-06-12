---
title: "Xorg 7.1 edgy  - degrading responsiveness overtime"
date: 2006-11-20
forum: Desktop Environments
---

### Post by mjreged on 2006-11-20
Hello to all community participants,
  I would like to bring everyones attention an observation i made that is recurring on my EDGY installation regarding performance.
I am a software developer for an construction company and i develop internal systems using UBUNTU.
I usually leave the system running 24H 7 Days, but since the installment of edgy, i noticed a huge performance decline when a system is not restarted within 24 hours. hit performance hit i believe is coming from the Xorg because scrolling is getting choppy, windows take longer to refresh and move etc...   

I have a DELL Dimension 2400 with 810 Intel graphics integrated,
my acceleration is enabled. 

Does anyone else experience the same issue ?

---

### Post by strange_cathect on 2007-10-26
Yes, I can second this problem.  I just installed 7.10 from the previous version and my internet scrolling is VERY wavy and choppy (like it used to be when you tried to load a web image in 1993 or something).  This is also a big problem in my Open Office.  Scrolling causes a jerky, wavy, choppy screen that is hard to precisely control. Very annoying.

---

### Post by underwog on 2007-12-21
I also have this problem. I run Folding@Home and it is just more then Xorg I think. My folding performance is 100% for about 24hrs, but after that performance drops slowly and reaches about 50% (my folding frame times double) around 36hrs from last reboot. I have all powersaving features turned off in the bios and uninstalled in Ubuntu; the computer is working on the same WU; it doesn't get better without a reboot. Inaddition EVERYTHING is laggy. Reboot and everything is fine. In the first 24hrs after a reboot even with Folding@Home running 4 threads (SMP client) there is not lag doing anything else.

When the system hasn't been rebooted and things are laggy I use the System Monitor to see if anything is hogging the CPU. It isn't. CPU time has been devoted to almost exclusively to Folding. Stopping the Folding doesn't clear up the issue either. Only a reboot does.

---


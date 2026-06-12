---
title: "Major disk usage discrepancy"
date: 2009-03-22
forum: General Help
---

### Post by dave_didlydodo on 2009-03-22
My Ubuntu disk partition appears to be almost full, according to the partition editor and disk usage analyser (see attached screenshot). Both say 77GB used, 5.5GB spare (82.5GB total). So I want to know what to delete or move to another partition. However, when I look at the detailed filesystem breakdown in disk analyser (see the ring chart) it says only **23GB** is used. :confused:  Anyone have any idea where the missing 54GB might have gone? Maybe that's what I can cut down or remove, if only I can find out what it consists of!  Surely it's not hidden operating system files... 

However, when I first run up the analyser, everything agrees - the one red ring shows the total filesystem size as 77GB, it's only when I ask it to 'scan filesystem' that the discrepancy appears.

I've checked that the disk usage analyser is only scanning the Ubuntu partition, not any others on the disk.  

Help!!

---

### Post by dave_didlydodo on 2009-03-22
Found the answer - you need to run the disk analyser (or something like filelight) in Terminal using sudo, so the analyser can see all the files that otherwise don't have read priveleges. 

Turned out to be a backup problem.

---


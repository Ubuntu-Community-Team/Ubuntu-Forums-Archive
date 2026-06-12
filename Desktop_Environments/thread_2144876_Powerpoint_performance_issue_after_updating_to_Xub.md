---
title: "Powerpoint performance issue after updating to Xubuntu 13.04"
date: 2013-05-13
forum: Desktop Environments
---

### Post by grahams on 2013-05-13
After updating from Xubuntu 12.10 to 13.04 I noticed that PowerPoint 2007 via Crossover (wine) became very slow and takes many seconds to refresh slides. Doesn't seem to be a graphics driver issue, as everything else seems to run just fine and gtkperf shows decent performance. 

Running Office 2007 in a VirtualBox VM on the same machine is very quick, so it seems to a wine issue.b

I was on Crossover 12.1.2 and updated to 12.2.0, no noticeable improvement. Note. Crossover 12.2.0 uses wine 1.5.15

Is this a known issue? Related to Wine?, lightDM, XFCE? Anything I can tune?

---

### Post by grahams on 2013-05-14
Solved by updating office 2007 to SP3 using the 2007 SP3 crossover tie. Now the performance is as expected.

---

### Post by grahams on 2013-05-14
.

---


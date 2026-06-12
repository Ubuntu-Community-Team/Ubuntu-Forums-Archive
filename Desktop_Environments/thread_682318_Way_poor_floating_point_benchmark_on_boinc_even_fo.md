---
title: "Way poor floating point benchmark on boinc even for linux"
date: 2008-01-29
forum: Desktop Environments
---

### Post by shadrach343 on 2008-01-29
My first installation of gutsy-gibbon yielded me less than 50% of the performance running boinc einstein@home than that of same system under XP.  Floating point benchmark was less than 1000 MIPS on a Athlon 64 X2 clocked at 2.7GHz, finishing jobs in about 25 hours.  I have three identically equipped systems,  Then it turns out my second installation on a different machine with exactly the same hardware ran slightly faster than the same windows machine.  It benched at 1900 MIPS and finished jobs in about 12 hours.  I ran it at this rate for several days and many jobs were finished at this rate and acknowledged.  After about the 3rd restart since installation, the performance went back to what I had seen before.  I tried using various clients and versions of the crunchers, but the problem is the system.  Is there a processor setting that is causing the performance loss?  How could I lose that kind of performance just from restarting the system (I had to move the optical drive to a different system).

---

### Post by Kougaiji on 2008-01-30
I'm having the same issue. It's benching at 1500MIPS when it used to do over 5000MIPS in previous installations (earlier versions of gutsy and also rt kernel).

The CPU barely seems to be working. What happened to BOINC?

EDIT: Looking at the system monitor while running, it seems like whenever one of my cores (running dualcore) jumps to a high percentage, the other goes really low, in attempt to have the two add up to 100% as opposed to having EACH core working at 100%. The system isn't even warm, i can't hear the fan working hard, so all this tells me the CPU is giving little, if any effort.

This was not always the case, as ubuntu outperformed my old vista partition by a vast amount, and performed significantly faster than xp64.

~running x64 boinc client on dualcore amd64 laptop.

---

### Post by Golem XIV on 2008-01-30
Check your CPU Frequency scaling monitor, maybe the cores have been throttled down to ~50% of their frequency unless there is a demand (that apparently does not include BOINC apps).  This is the default setting on my laptop, don't know if it would be the same on a desktop.

---

### Post by shadrach343 on 2008-01-30
That was the trick.  Thank you so much, now Boinc runs full speed.  Now all I have to do is figure out how to get it to run at my overclocked rate.

---


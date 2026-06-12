---
title: "Cannot generate useful backtrace debug info for crash reporting, Kubuntu panels"
date: 2016-10-09
forum: Desktop Environments
---

### Post by Peter_Brandon on 2016-10-09
I recently installed 16.04.1 Xenial on my computer.  I have since had numerous Plasma shell crashes in which my panels disappear (and restart) and something called "Crash Reporting Assistant" appears.  I'd like to help out by filing a report, but the backtrace part of the crash report dialog says "The generated crash information is not useful".        It offers a couple links to help my figure out how to generate useful reports.  One tells me that packages with debug info for plasmashell are missing.  I looked up the package for plasmashell, which is plasma-workspace, but plasma-worksapce-dbg was already installed. I then used synaptic to search for all files containing keywords 'plasma' and 'debug' and installed all of them (except for the plasma sdk dbg).  This had no effect--I still get the crash info not useful message.      The other link leads to a defunct web page, but it says to go to a community wiki.  After a few more steps, I get to here:  [https://community.kde.org/Guidelines_and_HOWTOs/Debugging/How_to_create_useful_crash_reports#Kubuntu](https://community.kde.org/Guidelines_and_HOWTOs/Debugging/How_to_create_useful_crash_reports#Kubuntu) .  There, it suggests I install kdelibs5-dbg.  That also has no effect.  I just added pkg-create-dbgsym, just had another crash, and again no difference.

---

### Post by Peter_Brandon on 2016-10-11
Bump....

---


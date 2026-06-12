---
title: "Will LXDE/KDE Save Memory? How Much?"
date: 2013-10-30
forum: Desktop Environments
---

### Post by Jeff_Berrian on 2013-10-30
Ubuntu 12.04 LTS: If I install LXDE, KDE or another lightweight environment and select to run it during a session, will I be saving memory resources? If so, approximately how much? 

I'd like to run Windows XP guest (virtualbox) and allocate as much memory as possible to the VM without degrading host performance. I have a limited amount of memory on this older machine (2GB). I figure if I load up LXDE, and launch XP guest I may squeeze out better performance from both host and guest however I am unsure if it's enough to notice an increase in performance/speed from what I am running now, default Unity + WinXP VM (?)

FYI: I am running a streamlined version of Windows XP as guest with several under-the-hood tweaks to services, regedits, etc. so that it can run as lightweight as possible.

Any opinions/suggestions? 

Much appreciated!

---

### Post by carl4926 on 2013-10-30
LXDE

kde is on a par with unity, so forget that

But: XP, really!

---

### Post by grahammechanical on 2013-10-30
What do you mean by lightweight? We can strip as much code out of an OS as possible but then we only create space on a hard disk. The bits of code that remain will still use memory when the code is run. This is unavoidable.

I would suggest that you experiment. We can install the Xubuntu, Kubuntu and Lubuntu desktops on Ubuntu but even though we are not logged in to Ubuntu (Unity) we may still be carrying a Ubuntu memory overhead. You may find that installing Xubuntu or Lubuntu may bring a lower memory usage than running Ubuntu even without an alternative desktop installed. Xubuntu may be a better choice as from its inception its purpose is to run on lower specified machines.

An other factor to keep in mind if you are looking for a performance increase is the roadblock of the graphic adapter. Can the graphic adapter cope with the graphic workload?

Regards.

Update: I have 1GB RAM and when I was running Ubuntu 12.04 memory usage with nothing loaded was just above 70%. I have since run 13.04 and 13.10 all through their development cycles and memory usage was about 10% - 15% less, a little over 50%. I am now running 13.10 that has been converted to Trusty Tahr (14.04 under development) and I am seeing another reduction in memory usage to 20% without any applications running. Right now I am running Chromium with two windows open, one for this site and another window playing a BBC radio program and System Load Indicator is saying that I am using only 559MB of that 1GB.

As regards memory usage things have improved for Ubuntu and derivatives based upon the latest versions. By 14.04 we will have to change our view of what is light and what is heavy and what versions of Ubuntu work better on older hardware.

---

### Post by buzzingrobot on 2013-10-30
KDE has a reputation for being something less than a light-weight interface.  However, the current version is at the end of a long period of bug fixes and enhancements.   You won't have much trouble finding reports that it uses much less memory than most people think.  Plus, it is very -- even annoyingly -- configurable, so users can disable many features to reduce memory use,

In the end, the only sure way is to experiment on your own hardware. Memory use varies depending on many variables, including the amount of available RAM. I.e., some tools will use more memory if it is available.

A focus on lightweight applications might be more useful.  Large applications like browsers typically consume more memory than things like kernels and desktop environments, so larger savings  may come from a wise app selection than from changing to a so-called light distribution.

---

### Post by walterorlin on 2013-11-02
LXDE will use less ram. Thing is having 10 or more tabs in a browser open will start to use a lot of memory.

---


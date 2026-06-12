---
title: "How to automatically enable or disable twinview"
date: 2011-02-12
forum: Desktop Environments
---

### Post by hartz on 2011-02-12
Is there a way to get Twinview to become active automatically when I plug in my second monitor?

I have a laptop and when at home I plug in a second monitor.  I can then extend the desktop (by enabling twinview) and it works fine.  When I suspend and subsequently resume somewhere else, (when the second monitor is no longer attached), I then need to first find the mouse pointer, often somewhere off on the other monitor (Sorry I left my mouse pointer at home :-)

Essentially I want Twinview to activate automatically when I plug the second monitor in, and to disable when I unplug the monitor.  Further more Ideally I want it to remember the screen resolutions and as a bonus put windows back to where they were (when and if possible).  I am sure other people must have encountered and solved this same niggling dilemma?

Thanx,
  _hartz

P.S. Info about my computer:

hartz@my-laptop:~$ lspci -v|grep -i nvidia
\01:00.0 VGA compatible controller: nVidia Corporation G84M [Quadro NVS 140M] (rev a1) (prog-if 00 [VGA controller])
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb
hartz@my-laptop:~$ uname -a
Linux BCX-laptop 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

---

### Post by hartz on 2011-02-14
It just occurred to me that Fn-F7 (The "hardware" switch to select the external monitor mode) should be a perfectly good method for enabling/disabling Twinview!

P.S. And Bump!

---


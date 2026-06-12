---
title: "How to switch from vesa to modesetting"
date: 2018-12-05
forum: Desktop Environments
---

### Post by Mark_Edwards on 2018-12-05
Hi all,

I'm fairly new to Linux so please bear with me. First a quick summary to explain what has happened!

I installed a new default build of Ubuntu 18.04, all good,  I then installed Mate as my desktop environment
Whilst installing that, i went off and did something else on the machine, and on checking back half an hour later, I found the terminal running the window had vanished. I wasn't sure what state the system was in, so I (stupidly) thought it would be sensible to remove the mate desktop package then reinstall it and watch it more closely. However on doing this and rebooting the machine, I ended up in raw text mode and no desktop at all lol !!

I surmised that installing mate, uninstalled gnome3, then because I removed mate as well I essentially ended up with nothing!

Anyway to cut a long story short, i've pretty much got it back up and running again, except only 1 of my 3 monitors is recognised (2 are display port, the other is HDMI. All 3 worked fine on the initial install when using Gnome)

Running inxi -G shows:
Display: server: X.Org 1.19.6 driver: vesa unloaded: fbdev,modesetting resolution: 1920x1080~N/A 

So due to my screw up, it seems the system is now set to using the basic vesa driver instead of the modesetting driver, which i think is the issue.

Can someone advise how to switch my driver to modesetting.

---


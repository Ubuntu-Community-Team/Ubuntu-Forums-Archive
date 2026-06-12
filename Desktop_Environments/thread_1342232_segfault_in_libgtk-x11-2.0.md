---
title: "segfault in libgtk-x11-2.0"
date: 2009-11-30
forum: Desktop Environments
---

### Post by teal42 on 2009-11-30
Hi everyone

I recently did a fresh install of Karmic (9.10) and after a few weeks had finally set everything up, and was pretty chuffed with my system.

Since yesterday I am suddenly having major problems with applications, nautilus and gnome-panels all crashing with a segfault in libgtk-x11-2.0 (error 4).

Most of the time the panels and nautilus crash within 1 or 2 minutes of logging into gnome.

Gnome is basically unusable and its the only desktop manager I have installed.

Any assistance would be super. 

Thanks
Warren

---

### Post by smani on 2009-11-30
What you could try doing is creating a new account and looking if the problem persists (that is you could see if it is a problem with the installed packages or with the personal configuration). If it works fine with a new user account, then you could try moving all configuration folders (the one beginning with a dot in your home folder, CTRL+H in nautilus to show them) in some other folder, and then restoring them one by one to find out which one causes the problem - if it is a configuration issue then you'll likely want to look closely at the .config and .local, as well as possibly .gnome*, .gconf* folders. If you do not care about you current configuration you could also just remove them (that won't affect which packages are installed).
If the problem also persists with a fresh configuration, then things are harder. One thing you could do then is obtain a backtrace of one of the applications that crash - see [https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace) - maybe the backtrace contains some hint on what's not working.

Cheers
smani

---


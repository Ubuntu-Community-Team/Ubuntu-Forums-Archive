---
title: "Gradual Startup Slowden in GNOME"
date: 2007-12-15
forum: Desktop Environments
---

### Post by fishexe on 2007-12-15
For some reason, GNOME has gotten slower to load in the last month or so.  I've only had this computer for about 2 months (ubuntu came pre-installed) and everything worked great for the first month...now it displays the splash screen for a long time (maybe 2-3 mins) when I log in, and it won't let me open any programs until it's gone...then once it goes my programs (even simple things like terminal and text editor) take a minute or two to open...once I've been logged in for about 10 mins, the problem goes away.

Any ideas on how this would arise?  Is there anything I need to check on my filesystem or config files?  How would I go about diagnosing the problem, since I have no idea which program is causing it to stall?

I am using Feisty on a Dell Inspiron 1420 and log in using the normal gdm method.

---

### Post by fishexe on 2007-12-28
By upgrading to 7.10 the problem was automatically fixed.  However, upon upgrade Nautilus began acting funny.   By which I mean, not running at all.
**sudo dpkg-reconfigure nautilus** did the trick however.

---


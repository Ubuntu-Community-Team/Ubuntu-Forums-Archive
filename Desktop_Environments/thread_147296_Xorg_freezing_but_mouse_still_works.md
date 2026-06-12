---
title: "Xorg freezing but mouse still works?"
date: 2006-03-19
forum: Desktop Environments
---

### Post by UbunT00L on 2006-03-19
I have a problem where Xorg in Breezy will freeze.  My keyboard will not respond and I am unable to switch to a terminal as a result.  However, my mouse seems to keep working, I can move it around the screen but nothing will respond to clicks.  Luckily, I am still able to ssh into the system, but I cannot kill X for some reason.  Typing in "sudo killall -9 X" doesn't seem to do anything, and I still see X when I look at "ps ax".  **edit** I am able to kill X using the kill -9 PID option.  **/edit** I am able to reboot though, which is what I have been doing.

These are the last lines I saw in the Xorg.0.log during a freeze:

```
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Got unexpected buttonTimer in state 0
```

Has anyone else experienced this behaviour?

---

### Post by poekie on 2006-03-23
Yup. I had the same problems when I used nvidia driver (videocard is GeForce FX 5200), with nv no problem whatsoever, but no glx as well. But as I don't really use glx I just keep nv. 
It was a problem for me in hoary but an updated nvidia driver solved the problem, problem came back when updating to Breezy and no solution to date that actually stops my screen from freezing.
Commenting out the load dri line etc, nothing worked.

---

### Post by UbunT00L on 2006-03-23
Well, commenting out the "load dri" and "load GLCore" lines in my xorg.conf seems to have fixed the problem.  I now have glx with direct rendering, and the freezing appears to have stopped (or at least it's stopped for the past 24 hours).

---


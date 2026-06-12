---
title: "KDE 3.5.9 ubuntu7.1"
date: 2008-05-08
forum: Desktop Environments
---

### Post by trburkholder on 2008-05-08
A couple of days ago, Hardy Heron was working more or less perfectly except for a small bug with my Sony mp3 player.

Since an update (I think to kde 3.5.9-0ubuntu7.1) , I haven't seen the kde login screen and haven't been able to use any kde programs.

For example:
kdeinit fails with a warning about libkparts.so.2 not found.
kontact won't open and complains about missing libvcard
kdm start, stop or restart hangs with a blank screen.

Am I missing a library?  kdelibs is installed 

I uninstalled and purged as much of kde as I could and reinstalled.  I also moved my .kde directory in case that was the problem.  I managaed to install ubuntu-desktop and Gnome is working, but I really prefer KDE.

Any suggestions would be greatly appreciated.

---

### Post by trburkholder on 2008-05-08
Ok, sometimes just writing down the problem shakes loose a solution.  

I downgraded kdelibs and kdelibs4c2a to 3.5.9-0ubuntu7 and that seems to have fixed the problem.

---


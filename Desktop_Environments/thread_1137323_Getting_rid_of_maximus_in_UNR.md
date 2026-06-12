---
title: "Getting rid of maximus in UNR?"
date: 2009-04-25
forum: Desktop Environments
---

### Post by pauna on 2009-04-25
Is there a way of getting rid of a running maximus short of removing the package?

I reinstalled my EEE PC 901 using Jaunty UNR from USB stick and switched from UNR view to classic Ubuntu. Some things broke but I was able to recover.

The only problem is maximus, which is still running in the background even when I have removed it from the "Startup Applications" (i.e. the old session). Yes, I have REALLY removed it from the startup. I even once put it back again and ended up with two maximus processes.

Killing maximus just causes it to automatically restart.

I have checked the no_maximize box in gconf-editor apps/maximus, but I still keep on getting random undecorated full screen windows (for example firefox). I'm sure there's a logic somewhere, but right now this is annoying.

BTW, I really hate programs that fail to honor "kill -9".

---

### Post by pauna on 2009-04-26
Well, it turned out I had at one point saved a session and maximus got sticky because it was running then. So I had to delete the appropriate desktop file from .config/gnome-session/saved-session/.

This took me several hours to understand and solve, including several tries in trying to edit .gconfd/saved_state etc.

---


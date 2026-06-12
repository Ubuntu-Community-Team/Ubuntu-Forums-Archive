---
title: "Daily Gnome-Shell compiling failures solved"
date: 2011-02-19
forum: Desktop Environments
---

### Post by puntigamer on 2011-02-19
Hi guys, 
I've seen, that many of you have errors and running issues with the daily Gnome-Shell build (2.9* from GIT).
I've solved some more problems, wich weren't listed on the WebUpd8 site:

Xulrunner problem:
Purge Mozilla Daily Builds PPA, and install Xulrunner-1.92-testsuite (+ ~-dev) instead

Crash in Activities menu:
The Shell is under development, so it doesn't support many video cards yet.
Try the closed source driver of your card, and update X settings. If you already have this driver, try to run the Shell without it!
And of course, don't forget to switch off Compiz!

Best wishes with the shell!

---


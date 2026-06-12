---
title: "AWN 0.3.9 crashes immediately"
date: 2010-02-17
forum: Desktop Environments
---

### Post by legatek on 2010-02-17
Hello,

I installed the latest version of AWN for Jaunty using the instructions on [this site]("http://www.webupd8.org/2009/10/avant-window-navigator-awn-04-available.html"). However, when I launch it it immediately crashes. Launching it from the terminal gives the following output:

```
monkey@monkey-Dell:/$ avant-window-navigator
Screen is composited
** (avant-window-navigator:29348): DEBUG: Updating dialog colours
** (avant-window-navigator:29348): DEBUG: Spawned awn-applet[29349] for "quick-prefs.desktop", UID: 1, XID: 73400388

** (awn-applet:29349): WARNING **: The desktop file '@APPLETDATADIR@/quick-prefs.desktop' does not exist.
** (avant-window-navigator:29348): DEBUG: Spawned awn-applet[29351] for "taskmanager.desktop", UID: 3, XID: 73400390

** (awn-applet:29351): WARNING **: The desktop file '@APPLETDATADIR@/taskmanager.desktop' does not exist.

```

I can run compiz or not, it gives the same errors. I can't find the files taskmanager.desktop or quick-prefs.desktop anywhere on my system. Does someone have an idea what's going wrong?

---

### Post by coolphoenix on 2010-02-18
having the same problem with karmic, fresh install, awn from ppa... maybe trunk is just broken

---

### Post by igrok2 on 2010-02-18
:popcorn:  same here, hopefully it will get fixed soon?

---

### Post by mpiermar on 2010-02-18
I had this problem too.  I went into awn-settings and added some applets.  There were no active ones by default. Once I added the MainMenu, Launcher/Taskmanger, etc, it all started working.

---

### Post by legatek on 2010-02-18
That did the trick. Thanks a lot.

---

### Post by litemirrors on 2010-02-18
The real solution is to ditch that dock and use Cairo Dock, mainly because it's better :)

---


---
title: "run level question"
date: 2006-03-20
forum: Desktop Environments
---

### Post by rfruth on 2006-03-20
Ubuntu is fine but (ya knew that was coming) when I switch run levels (Ctrl-Alt-F1) I *must* login as root and *rm* /tmp/.X0-lock file before startx will run, is there an easier way ? (yes I want to run X in two different windows)

---

### Post by jpkotta on 2006-03-21
Those are not "run levels", they're virtual terminals (VTs).  Run levels are sort of overall modes that the computer runs in, e.g. boot up, failsafe, normal, shutdown, etc.  

You should not delete that lock file.  It's there for a reason.  And you shouldn't need to log in as root to start a new X server.  Post back if you still need to do that with these instructions.

There are many ways to do what you want.  The simplest is ```
startx -- :1
```which will start a new X server on display :1 (the default is display :0).  Run this from any VT as yourself, not root.

Another, probably better way is to use ```
gdmflexiserver
```.  Run it while in X already, it won't work from a VT.  Try ```
gdmflexiserver -n
```to get an Xnest session ("X in a different window").

---

### Post by rfruth on 2006-03-21
Wow thanks ya learn something every day, startx -- :1 works for me !

---


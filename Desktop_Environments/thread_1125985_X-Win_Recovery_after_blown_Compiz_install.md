---
title: "X-Win Recovery after blown Compiz install"
date: 2009-04-14
forum: Desktop Environments
---

### Post by OldManRiver on 2009-04-14
All,

Installed Compiz Fusion, which blew and I got stuck where the:

Code:

sudo dpkg-reconfigure xserver-xorg

Command does not recover me.

All my apps go to 0,0 (upper left corner of the screen) and I can not even use anything needing input, such as the FF browser as the input fields are all locked and none of the screen have the upper banner, that lets you move them, so all are stuck at position 0,0 and they pile on top of each, not allowing any nav from app to app.

Thank goodness "Terminal" still works, but the Ctrl + F1, ... no longer call secondary command line sessions.

I hate to have to do a complete rebuild on this machine.

Help please!

Thanks!

OMR

---

### Post by OldManRiver on 2009-04-19
All,

There does need to be an effort to put together a recovery from this, but since I got no response I personally reloaded my entire OS from scratch, so got around this.

However since that may not be a viable option to some users, an effort to have a recovery from Compiz is needed.

OMR

---

### Post by calrogman on 2009-04-19
You can boot your system in single user mode, drop to a root terminal and run
```
aptitude reinstall xorg
```
which probably would of reconfigured everything which depends on xorg as well.

Sorry I didn't find this post earlier, it could of saved you a lot of work. :(

---

### Post by OldManRiver on 2009-05-16
> **calrogman said:**
> You can boot your system in single user mode, drop to a root terminal and run
```
aptitude reinstall xorg
```
which probably would of reconfigured everything which depends on xorg as well.

Sorry I didn't find this post earlier, it could of saved you a lot of work. :(

Cal,

Nope would not work, never seen Linux lock before where you could not get to a terminal session with Ctl+F2 or something else.  Notice on the 8.04 that X-Win runs in TTY1 on Ctl+F1 and all other TTY sessions are disabled.  Found that out after rebuilding the machine with recover from install CD.

Need to find something to turn these back on so I can pop out of X-Win, when it hangs like that again.

OMR

PS

My Bad, working with Ctl+Alt+F1...; but having to do another recovery as now some exteraneous string keeps inserting itself at the command line in all terminal session, which I can not escape from.

OMR

---

### Post by OldManRiver on 2009-05-16
Help please

---

### Post by OldManRiver on 2009-08-22
All,

Resolved this in thread:

[http://ubuntuforums.org/showthread.php?t=1139759&page=2](http://ubuntuforums.org/showthread.php?t=1139759&page=2)

Thanks!

OMR

---


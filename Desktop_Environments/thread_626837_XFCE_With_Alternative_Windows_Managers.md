---
title: "XFCE With Alternative Windows Managers"
date: 2007-11-29
forum: Desktop Environments
---

### Post by Mark76 on 2007-11-29
I'd quite like to see how Xubuntu would look running any of the alternative windows managers available in the repos (fluxbox, Enlightenmnet, IceWM, etc).  Is there anyway of doing that?  I know you can install them and then choose them at start up, but I'm pretty sure they're just running by themselves; not as part of Xubuntu.

---

### Post by kellemes on 2007-11-29
> **Mark76 said:**
> I'd quite like to see how Xubuntu would look running any of the alternative windows managers available in the repos (fluxbox, Enlightenmnet, IceWM, etc).  Is there anyway of doing that?  I know you can install them and then choose them at start up, but I'm pretty sure they're just running by themselves; not as part of Xubuntu.

Not really sure what you mean..
A window/desktop-manager can not be used without an OS (like Xubuntu is an OS).
So, starting up IceWM on Xubuntu will normally give you the same look as starting it up on Fedora or Arch.

---

### Post by PeterJS on 2007-11-29
If you're not running compiz. Open a terminal and try:
```

killall xfwm4
*windowmanagernamehere* &

```

Careful though, if your terminal looses focus when you have no window manager you're kinda hosed and need to restart X.

---

### Post by Mark76 on 2007-11-29
I'm running Compiz :o

---

### Post by PeterJS on 2007-11-29
Then it'd be something with the window decorator plugin, sorry I can't be more specific, but my personal machine is out of commission right now. Stupid power surges, I really should know better :(

---

### Post by jviscosi on 2007-11-30
I haven't used Compiz in a long time but didn't there used to be a place in compiz manager where you could set the fallback window manager, and then you could also tell it to switch to the fallback window manager?

Also, some window managers support a --replace flag when you start them that's supposed to make them replace the currently running window manager.  Not sure how gracefully compiz handles such a request.

Anyway, you could get a similar effect by just running the window manager you want to try, plus xfce-mcs-manager and then whatever XFCE components you want (like the panel, xfdesktop, etc.)  Of course if you run xfdesktop on top of, say, Fluxbox, you'll get the XFCE right-click menu instead of Fluxbox's, but that might be what you want.  How you auto-start programs with the window manager will vary by WM of course.

---

### Post by urukrama on 2007-11-30
If I  use XFCE, I always use it with Openbox. It is light, and I love Openbox as a window manager!

To do so, have a look [here]("http://icculus.org/openbox/index.php/Help:XFCE/Openbox").

---


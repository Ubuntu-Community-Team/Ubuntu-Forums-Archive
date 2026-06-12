---
title: "Konsole text selection doesn't work anymore"
date: 2009-05-27
forum: Desktop Environments
---

### Post by alSee on 2009-05-27
Since my KDE updated to version 4.2 the strange Konsole behavior appeared. When some mouse-sensitive application runs inside Konsole (such as mc, vim etc.) it is impossible to select a text with mouse (and copy it into clipboard) by holding the shift key (which prevents mouse events from being handled by app). That was possible in KDE 4.1 and before. How to get the "old style" mouse behavior in Konsole?

---

### Post by shirsch on 2009-05-31
I'm having the same problem.  I rely heavily on being able to cut-and-paste text out of Midnight Commander under konsole and this simply does not work under KDE4.

Will open a bug report, for all the good that's likely to do.

---

### Post by LStranger on 2010-04-02
I found how to reproduce it. After X-server is restarted Konsole text selection works again. After you logoff from KDE4 session and logon again - it does not! Quick workaround for this bug is to uncomment and change setting in your /etc/kde4/kdm/kdmrc file (section [X-:*-Core]): TerminateServer=true. Don't know where to bugreport this issue and why exactly can that happen, it's definitely KDE4 bug.

---

### Post by bwooster47 on 2010-05-15
Well, konsole text selection is completely broken - it does not even work normally (no mouse app, just konsole).

Restarting X server and then konsole will allow left-mouse select and middle-mouse paste work. But within a few minutes, it stops working - can select, but not paste. Exiting and restarting X server fixes it for a minute or two.
Other applications work fine - firefox, xterm, etc

This is bad... not sure where to report the bug too. Running kubuntu 9.04, with all updates.

Tried the TerminateServer workaround mentioned above - no luck (why would that fix things anyway? it just restarts X server on logout, does nothing to konsole)

---


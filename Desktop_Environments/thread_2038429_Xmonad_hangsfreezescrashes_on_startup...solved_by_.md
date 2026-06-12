---
title: "Xmonad hangs/freezes/crashes on startup...solved by a hack!"
date: 2012-08-06
forum: Desktop Environments
---

### Post by patanjalimuni on 2012-08-06
**Summary**: The tiling window manager Xmonad was crashing on startup (Ubuntu 12.04). This was solved by editing the /usr/share/xsessions/xmonad.desktop file, changing it to start a script which first sleeps for one second, then starts Xmonad. 

**Details**:
I'm using "pure Xmonad", not Xmonad with Gnome.
After installing Xmonad, I logged on with no problem. Within Xmonad I created a simple ~/.xmonad/xmonad.hs startup file, compiled it with xmonad --recompile, and restarted xmonad with mod-q. Everything worked fine, and the simple changes in my startup file worked.

But after rebooting it would hang. In a normal Xmonad start, after typing my password, the password dialog disappears leaving the Ubuntu background image (or whatever I specify).
But now, the password dialog never disappeared, giving the false impression that Xmonad wasn't loaded. But it was possible to type a few Xmonad commands, for example opening a file with dmenu--but soon everything hangs. Actually the mouse moves, but there is no response to mouse or keyboard. (Though the system does respond to 'magic sysreq' key combinations like alt-Sysreq-k).
As an experiment, I tried logging on as root. No problems.
Also, remembering that I had successfully recompiled my xmonad.hs file from within xmonad, I tried (a) logging in to a different window manager (i.e. Unity), (b) moving the ~/.xmonad/* files somewhere else, (c) successfully logging in with xmonad, (d) moving the ~/.xmonad/* files back, (e) restarting xmonad with mod-q. Presto! Everything worked. This made me think that *timing* was an issue, hence the idea of sleeping for a second before starting.

I just changed the /usr/share/xsessions/xmonad.desktop file, so that the "Exec=xmonad" line now reads:
```
Exec=xmonad-start.sh
```And I created the xmonad-start.sh script referenced in the xmonad.desktop file:
```
#file xmonad-start.sh, made executable.
sleep 1
xsetroot -grey #just to set background color
xmonad
```**Why does this happen?**
I know zilch about Linux programming, but speculate that ubuntu is starting xmonad in a process or thread different from the one which is closing down the login dialog. Otherwise, the login dialog would always have disappeared. Maybe the Ubuntu developers failed to foresee the implications of a window manager like Xmonad loading so fast. Even on my single-core processor, Xmonad in its own process could finish loading before the other processes finish their job, somehow making calls which create a conflict.
In view of the fact that the "sleep" hack solves it, I have no idea why logging in as root would have circumvented the problem, unless that somehow changes process priorities(?). Also have no idea why the problem would be there only in the presence of a startup file; maybe the recompiled version loads even faster??

Anyway, I hope this helps someone, & certainly welcome any further insights.

---


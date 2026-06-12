---
title: "Screen blank after 10 minutes of inactivity - SOLVED"
date: 2009-07-25
forum: Desktop Environments
---

### Post by drucer on 2009-07-25
Hi,

those of you who are trying not so common X window managers like XMonad on Ubuntu Jaunty might find themselves struggling with screen blanking problem. It seems like the screen goes blank after 10 minutes of inactivity and it has nothing to do with Xscreensaver, so even if Xscreensaver is not even running this happens. This appears to be XServer feature and here is how you can disable it.

These instructions are for advanced users, so novice users should not try to do this.

Edit /etc/X11/xorg.conf file with your favorite text editor (remember to use sudo, because the file is owned by root) and add the following section, save the file and restart X or your computer.

Section "ServerFlags"
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"
Option "DontZap" "false"
EndSection

I'm sharing this information through this forum so people are able to find this information easily with search functions, because this is very poorly documented feature and a lot of people seem to be having problem with this and are wasting several hours trying to find solution to this problem.

---


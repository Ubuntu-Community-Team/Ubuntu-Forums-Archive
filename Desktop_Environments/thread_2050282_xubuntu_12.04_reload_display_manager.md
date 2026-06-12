---
title: "xubuntu 12.04 reload display manager"
date: 2012-08-30
forum: Desktop Environments
---

### Post by talkingtek on 2012-08-30
I'm not able to reload display manager with the command:
sudo service lightdm restart or
sudo service xdm restart
 
What's the right command to reload Xubuntu 12.04.  I don't want to restart every time when I made a change.
 
thanks!

---

### Post by LewisTM on 2012-08-30
You can press Alt-SysRq-K to kill the X server and go back a fresh login prompt (which should be LightDM).
**sudo pkill X** should also work.
**xfce4-session-logout --logout** would be preferable in any case.

Cheers!

---


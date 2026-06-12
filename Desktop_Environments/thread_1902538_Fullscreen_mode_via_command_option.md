---
title: "Fullscreen mode via command option?"
date: 2011-12-31
forum: Desktop Environments
---

### Post by audeshmukh on 2011-12-31
Hi,

I am running Xubuntu Karmic with Xfce 4.6.

My objective is - to run an application on startup using a shell script in fullscreen mode. The auto-start is working fine. However, the Xfce menubar and system clock are visible. I want my startup application to cover entire portion of the screen.

For ex. I can switch the Xterm window (or any other window) to full screen mode by pressing Alt+Space and then select fullscreen from the menu.

Is there command option where I can specify such that the window should open in fullscreen mode?

---

### Post by 2F4U on 2011-12-31
I don't know if there are specific options available for XFCE, but for X in general, this may be interesting for you:

[http://ubuntuforums.org/showthread.php?t=1124561](http://ubuntuforums.org/showthread.php?t=1124561)
[http://linux.die.net/man/1/wmctrl](http://linux.die.net/man/1/wmctrl)

---

### Post by audeshmukh on 2011-12-31
Thanks a lot. I am now able to make the window fullscreen using commands xwininfo and wmctrl as mentioned in the thread that you suggested.

Thanks again.

---


---
title: "Latest X and WINE updates make gdm restart"
date: 2007-01-10
forum: Desktop Environments
---

### Post by jagolis on 2007-01-10
Hi all, when I installed the latest X org and WINE updates today 1-10-07, I restarted and I got a panel is already running message, and then a tenth of a second later, I get kicked back to login. Either X or gdm restarts, I can't really tell.

Then, adding to this situation, whenever I try to run WINE on anything (including a simple console win32 app), the same X or gdm restarts, and I get kicked back to login. There's nothing in any standard log files that mentions a crash, nor does saving the stderr/out of WINE when running.

Anyone else have these kind of issues with the new updates?

---

### Post by skimitar on 2007-01-11
Hi

Reinstall your video drivers to fix it.

[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

---

### Post by jagolis on 2007-01-11
That was it. Many thanks.

I do (after the fact) remember that any updates to X, and you have to reinstall the video drivers.

---


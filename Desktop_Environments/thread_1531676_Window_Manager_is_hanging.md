---
title: "Window Manager is hanging"
date: 2010-07-15
forum: Desktop Environments
---

### Post by coolman5001 on 2010-07-15
Within the past week or two, my window manager has started hanging.  All input takes several seconds before it appears on screen (including text entered in fields, changing focus between windows, moving windows - anything).  Sound appears to work in real time.

This behaviour occurs seemingly at random after being logged in for some length of time, and can usually be solved by logging out (at which point a dialogue pops up warning that the application "Window Manager" has stopped responding) or by ```
$ sudo pkill Xorg
```, and then logging back in.

I'm not sure which commands to run or which log/configuration files to check for errors.  How can I figure out what's causing these hangs and fix the problem?

Thanks in advance!

---


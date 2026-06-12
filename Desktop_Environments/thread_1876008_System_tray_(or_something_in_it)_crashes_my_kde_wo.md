---
title: "System tray (or something in it) crashes my kde workspace"
date: 2011-11-05
forum: Desktop Environments
---

### Post by megamasha on 2011-11-05
This is very annoying, and I'm on the verge of re-installing my system, but I hope someone can give me an alternative.

I was browsing the web as you do, and then kde plasma workspace crashed.
The desktop background disappeared (went black), then came back again, but my main panel (i.e. start bar) had disappeared.
Now it's gone and I can't get it back.
I have tried the following:

Right-click background -> add panel -> default panel...
crashes again, desktop goes blank, then reloads (panel is still missing).

Right-click background -> add panel -> empty panel...
empty panel appears.

Add Launcher (K button) to panel...
K button adds fine.

Add task manager to panel...
Task manager adds fine.

Add digital clock to panel...
Clock adds fine.

Add system tray to panel...
crashes again, desktop goes blank, then reloads (once again, panel is missing).

Every time I try to add a system tray, the desktop reloads and the panel vanishes.

I have tried reinstalling all packages related to kde workspace.

Are there any configuration files I can delete to reset the system tray?

Any suggestions anyone, please!?

MM

By the way, installing debug packages to create a useful backtrace for the crash would take up more disk space than I have free. :-|

Edit: Never mind, I found the following bug which seems to explain my problems: [https://bugs.kde.org/show_bug.cgi?id=277367](https://bugs.kde.org/show_bug.cgi?id=277367)

---


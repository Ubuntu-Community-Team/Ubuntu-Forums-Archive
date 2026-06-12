---
title: "AWN dock, same launcher, multiple icon issues"
date: 2011-09-14
forum: Desktop Environments
---

### Post by NattyNoobCake on 2011-09-14
i use ubuntu 11.04 classic 64 bit with AWN instead of the bottom panel and i have an issue
whenever i have a launcher that opens with a splash screen (netbeans and eclipse in my case), the launcher icon blinks but then another icon with the same image pops up. Then, that icon becomes the window icon for that program. I want to change this so that only one icon is used and multiple ones aren't created on the dock. I tried choosing show "only launchers" but then the window icon disappears.

---

### Post by Copper Bezel on 2011-09-15
I don't use either of those apps, but there's a similar problem with the OpenOffice suite. It has to do with the identifier the dock uses for the window, which in AWN's case is assumed to be the same as the launcher command. I don't know of any way to fix this directly.

You might try replacing the Launcher/Taskmanager with DockBarX, for which you can find a PPA _[here]("https://launchpad.net/~dockbar-main/+archive/ppa")_. It provides the same features and quite a few more, although many of them have to be set from its own settings manager (rather than through AWN's.) Most importantly, it keeps identifiers and commands separate (like the new Unity launcher does) and either shouldn't produce this problem, or can fix it if it does. (Right-clicking a launcher icon allows you to set its identifier to that of a running window.) You need two packages - dockbarx and awn-applet-dockbarx.

Thanks!

---

### Post by NattyNoobCake on 2011-09-15
got it working just fine, amazing applet, thanks a lot!

---

### Post by Copper Bezel on 2011-09-15
Sweet. = ) Just mark the thread as solved, Thread Tools at the upper right.

---


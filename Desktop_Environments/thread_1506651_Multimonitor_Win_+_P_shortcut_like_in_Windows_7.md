---
title: "Multimonitor: Win + P shortcut like in Windows 7"
date: 2010-06-10
forum: Desktop Environments
---

### Post by jure1873 on 2010-06-10
I like a lot the keyboard shortcuts that are available in Windows 7 for managing windows across multiple screens and would like to replicate them in ubuntu.
So far I created shortcuts for moving windows from one screen to another.

WinKey + Left: Move active window to the left screen
wmctrl -r :ACTIVE: -e 0,0,-1,-1,-1

WinKey + Right: Move active window to the right screen
wmctrl -r :ACTIVE: -e 0,1280,-1,-1,-1

Now when you press WinKey+P in Win7 you get a nice menu where you can select if you want only monitor1, monitor2 or both.

I would like to at least create shortcuts to switch between these modes. For example bind WinKey+1 to turn only monitor1 on, WinKey+2 for m2 and something else to have both monitors on. Any ideas?

---

### Post by jure1873 on 2010-06-10
If anyone else is having the same problems:

arandr is in the repos and it allows you to graphically create various randr configurations, save them to bash files and then create keyboard shortcuts for gnome that switch between them.

---


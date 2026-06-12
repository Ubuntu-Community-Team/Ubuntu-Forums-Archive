---
title: "xubuntu autostart on specific desktop"
date: 2007-01-27
forum: Desktop Environments
---

### Post by hoodwink on 2007-01-27
Hello folks. I'm running xubuntu-desktop on a feisty system, and it works great.

I have one problem, and this is common to all ubuntu variants and versions. The gnome and kde session managers will restart Firefox (but not other Mozilla variants) after a shutdown on the desktop where it was last running. Xubuntu will not restart Firefox automatically after a shutdown.

I have tried using the xfce autostart function as a workaround, but autostart starts Firefox on the last desktop used by session restart (I have two terminal sessions that are restarted). I can't find any options in autostart to direct the startup to a specific desktop.

There are a few older threads that discuss similar functionality on gnome using the wmctrl program. wmctrl enables cooperative window managers (xfce is one) to move a window to a specific desktop and to perform lots of other wm-related functions.

Does anyone have a clue how I might be able to trigger the appropriate wmctrl functions for a program started automatically by xfce?

---

### Post by tweedledee on 2007-01-31
Creating a script to launch firefox instead of running it directly should work, something like this:
```
#!/bin/bash
firefox
# now wait for it to load
sleep 10
wmctrl -x -r firefox-bin -t 1
```
Change the number in the last line to the #-1 of the desktop you wish to move it to.

devilspie is another choice, which is actually designed to move/position/etc windows upon startup, but it is a little harder to learn initially.

---


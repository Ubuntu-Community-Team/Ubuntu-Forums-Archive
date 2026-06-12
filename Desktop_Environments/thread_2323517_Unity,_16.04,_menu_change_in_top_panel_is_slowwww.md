---
title: "Unity, 16.04, menu change in top panel is slowwww"
date: 2016-05-05
forum: Desktop Environments
---

### Post by aeronutt on 2016-05-05
I've been a gnome-shell user for years, but am strongly considering switching to Unity. All was looking good...but...

If I have 2 or more full-size windows running, and switch between the two, the top panel is VERY slow in updating the menu to the new window that's on top. As in 5-10 seconds, or more. Seems odd.

Help!

---

### Post by aeronutt on 2016-05-06
A quick update.  

The top panel shows the correct menu when:
- I switch windows using alt-tab
- I switch windows by selecting the top window via clicking on the icon in the launcher
- if I set window behavior to "appearance->behavior=in menu bar"

So it appears, my problem only occurs when using a hot-corner to view and select a particular window.
Still, I love using a hot-corner to select a window, and can't come to using Unity if I can't find a fix for this.

It's extremely frustrating to have a full size window on top, and not have access to its menu!

---

### Post by aeronutt on 2016-05-07
Anyone?  This is kind of a show stopper for me for Unity.  I can move a window to the top, work in it for 10s of seconds, put my mouse over the panel, and the panel will STILL show the menu for the previous window.

Settings are :
Under Settings/Appearance
 -Show the menus for a window: In the window's title bar (this is needed because I use GIMP, and GIMP doesn't seem integrated into Unity)
 -Menus Visibility: Always displayed
Under Window Manager/Additional
 -Focus Mode: Mouse

Such a basic thing to ask Unity to do..show the right window menu!

---

### Post by howefield on 2016-05-07
Can't replicate your problem but there were a few reported issues with menus during the 16.04 development cycle.

May be worth looking at this thread.. [http://ubuntuforums.org/showthread.php?t=2319736](http://ubuntuforums.org/showthread.php?t=2319736) 

PS. Right clicking in the GIMP image window will give you access to the menus, not a solution, just offering as a workaround.

---

### Post by aeronutt on 2016-05-07
Thanks for trying to replicate!

If I set menus for a window to 'in the menu bar' and menus visibility to 'display on mouse hovering', all works as it should.  Setting GIMP to single window mode makes that work ok too.....
All windows managers / desktops have their nuances I guess. :)

---


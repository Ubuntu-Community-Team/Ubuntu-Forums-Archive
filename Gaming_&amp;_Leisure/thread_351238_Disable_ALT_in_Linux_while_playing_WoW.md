---
title: "Disable ALT in Linux while playing WoW"
date: 2007-02-01
forum: Gaming &amp; Leisure
---

### Post by chadk on 2007-02-01
In World of Warcraft, many add-ons use the ALT key as a modifier but in Linux the ALT key does other things... in WoW for example, one add-on wants me to use ALT click to drag the item around but if I do that it moves the entire WOW window.  ALT Drag isn't the only ALT combo I want to use in-game. 

I'd like the alt key to function as intended when I'm not in WoW but I want WoW to have full control over ALT when I'm in the game.

---

### Post by chadk on 2007-02-07
Is there no way to do this?

---

### Post by Sammi on 2007-02-07
I think you can justify asking this question in the "[Desktop Environments]("http://www.ubuntuforums.org/forumdisplay.php?f=132")" support room, as it's really more of a Gnome question than a game question.

---

### Post by leanbeef on 2007-02-13
Go to System > Preferences > Windows, and set the movement key.

---

### Post by chadk on 2007-02-23
Thanks leanbeaf.

Is there any way to do this via shell script?  I would really prefer to just disable it while playing WoW then enable it when I quit WoW.

---

### Post by cb951303 on 2007-02-24
I needed the same thing for Diablo II.
There is another way to do this but It may cause another problems.
Go to winecfg window. "add application" and select wow's exe. then go to graphics tab and unselect "Allow the window manager to control the windows". It will disable the window manager for WoW. Wine will handle the window management so it may cause other problems... If it does let us know...
here is a screenshot

---


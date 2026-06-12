---
title: "Starcraft battlenet"
date: 2008-06-16
forum: Gaming &amp; Leisure
---

### Post by MegaUA on 2008-06-16
When ever i attempt to access battlenet i turns black, there is a place to put in user account name, and buttons for a new account, however wine freezes, what can i so to fix this

---

### Post by cogadh on 2008-06-16
You probably can't. Battle.NET doesn't really work in Wine.

BTW - There is a [Wine Sub-forum](http://ubuntuforums.org/forumdisplay.php?f=313) where questions like this should be posted.

---

### Post by MegaUA on 2008-06-16
i've seen multiple people access it, i've also seen the same problems, i did see a solution but i forget where it was, i ignored it because i was having problems getting the sound to work. (thats resolved now) and yes i noticed that after

---

### Post by cogadh on 2008-06-16
Known issues with Battle.NET:
Warcraft3 Battle.net Doesn't work (Needs AcceptEx) - [http://bugs.winehq.org/show_bug.cgi?id=9787](http://bugs.winehq.org/show_bug.cgi?id=9787)
starcraft doesn't display battle.net menus correctly - [http://bugs.winehq.org/show_bug.cgi?id=2467](http://bugs.winehq.org/show_bug.cgi?id=2467)
Starcraft/Diablo/Battle.net crashes from font metrics problem - [http://bugs.winehq.org/show_bug.cgi?id=5253](http://bugs.winehq.org/show_bug.cgi?id=5253)
StarCraft Battle.net-Hitting the Browse button hangs the game - [http://bugs.winehq.org/show_bug.cgi?id=9500](http://bugs.winehq.org/show_bug.cgi?id=9500)

That last one sounds remotely similar to the problem you are having and it is reported it can be fixed by just unchecking "Allow the window manager to control the windows" in winecfg. It could also be related to the menu display problem, which I don't believe has a real fix.

---

### Post by PrimoTurbo on 2008-06-16
I wouldn't play on battlenet with wine, I got banned before.

---

### Post by disturbedite on 2008-06-17
> **PrimoTurbo said:**
> I wouldn't play on battlenet with wine, I got banned before.
do you mean they systematically ban linux (wine) users? or were you using a pirated version of a game?

---

### Post by PrimoTurbo on 2008-06-17
No I was using legitimate retail version of Starcraft, after about a week of playing through wine I was banned. This was right after an update also, because they are always looking for people using cheats and sometimes they detect things like wine as cheats.

---


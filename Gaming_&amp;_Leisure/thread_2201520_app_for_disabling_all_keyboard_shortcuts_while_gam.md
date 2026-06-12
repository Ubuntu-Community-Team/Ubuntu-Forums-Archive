---
title: "app for disabling all keyboard shortcuts while gaming"
date: 2014-01-24
forum: Gaming &amp; Leisure
---

### Post by dainis on 2014-01-24
i tried heroes of newerth on my ubuntu 13.10 and was amazed how much new shortcuts i have discovered while playing the game. but i dont want that exploration anymore while gaming so i am searching for possibility to disable all keyboard shortcuts that can ruin my game.
any software that disables it? and when gaming ends enable them all again.

thanks!

---

### Post by ajgreeny on 2014-01-24
Not sure about ubuntu but in Xubuntu the keyboard shortcuts config file is .config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml.  Look for something similar in ubuntu if that's what you use.

It should be easy enough to write a script that renames that file as a backup when you start a game and then restores the name when you close the game; that may do the trick as long as a logout is not needed to disable the shortcuts after the renaming.

---


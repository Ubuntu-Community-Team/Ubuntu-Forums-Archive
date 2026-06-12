---
title: "X simply for gaming?"
date: 2005-08-04
forum: Gaming &amp; Leisure
---

### Post by Nightblade on 2005-08-04
Hey!

I'm looking for a way to start only X, for gaming only. No gnome or any side-apps, only X and what's needed to play my games. Like a terminal to enter the game etc. Must give a real performance boost right?

---

### Post by varunus on 2005-08-04
Can't you just choose "failsafe xterm" from the Sessions menu at the Login Screen?  This will bring up just a terminal and a blank X server.  You can start your games by typing in their name.  You may need to have a window manager running for games to work.  If you want the lightest weight one possible, type in:
sudo apt-get install twm

Then, when you open the failsafe xterm, type:
```

twm&
nameofgametoplay
```

Good luck.

---

### Post by Mishura on 2005-08-04
I never noticed a performance difference when trying games like UT2004 with twm and KDE.  But thats just me.  You start noticing differences when you have apps open like amaroK or anything else thats resource intensive.  Its a "Milage will vary" deal.

---

### Post by drizek on 2005-08-04
[QUOTE=Mishura]I never noticed a performance difference when trying games like UT2004 with twm and KDE.  But thats just me.  You start noticing differences when you have apps open like amaroK or anything else thats resource intensive.  Its a "Milage will vary" deal.[/QUOTE]
 I think its more cpu dependant than anything else. if you get rid of all the cpu hungry apps, youll be fine(maybe just use another account in gnome/kde). But the memory will be freed up when you open the game, and kde/whatever will be put in swap.

---

### Post by endy on 2005-08-04
You may want to check out a little how to I made. It's so you can run games from a single command without gdm or gnome etc running as it starts a new xserver specifically for the game. But it can also be run from the desktop.

[http://ubuntuforums.org/showthread.php?t=51486](http://ubuntuforums.org/showthread.php?t=51486)

I hope it's of some use to you :)

---


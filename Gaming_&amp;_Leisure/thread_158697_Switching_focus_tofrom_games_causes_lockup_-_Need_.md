---
title: "Switching focus to/from games causes lockup - Need help."
date: 2006-04-11
forum: Gaming &amp; Leisure
---

### Post by Pas3n7 on 2006-04-11
I'm running Ubuntu 5.10 with kernel 2.6.15-ck1. I'm running on a Dell Ispiron 1150 notebook with the Pentium 4 Mobile 2.8Ghz, and 512MB of RAM. 

The problem is, whenever I switch to or from anything using 3D graphics (it has happened with both native Linux games, and games running through Wine), The screen locks up, then goes blank. Then the mouse cursor displays the "waiting" animation, then the pointer, then nothing. It cycles through all of those until I manually power it down.

I'm really lost on this, and searching both the forum and google turned up nothing. I'd appreciate any help you all can give.

-Pat

---

### Post by minisori on 2006-04-12
Do you mean when doing ALT+TAB? 

If you preffer you can run the games in another X. It just a workaround. Do this:

sudo X :1 -ac & DISPLAY=:1 game

This will run the game in another X, so you can switch between your desktop (CTRL+ALT+F7) and the game (Probably CTRL+ALT+F8 ).

---

### Post by Pas3n7 on 2006-04-13
It happens with alt-tab for fullscreen and windowed games. Also by minimizing/restoring a windowed game, or just clicking on a different window. I'll try out what you said though, thanks for the advice.

-Pat

---


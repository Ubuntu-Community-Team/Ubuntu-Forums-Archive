---
title: "minimizing full screen games"
date: 2006-04-26
forum: Gaming &amp; Leisure
---

### Post by Artist22405 on 2006-04-26
ok dumb noob question when I play et someytimes I get an im from my wife and I would like to know how to minimize the game to answer her im real quick then go back to my game

---

### Post by Jazzyjazz on 2006-04-27
I'm actally interested in this one as well :confused: ALT+Fx doesn't do anything when I run UT2k4 in window mode and I can't get out of the play screen at any time.

---

### Post by minisori on 2006-04-27
Alt+tab or minimize doesn't work so well with games.

Try this workaround.. edit xorg.conf and add into the Section "ServerFlags" the Option "AllowDeactivateGrabs" "true". Now when you press CTRL+ALT+/ it would release the mouse focus so you could answer.

Another workaround would be to start another X runing the game, so you can switch between desktops with CTRL+ALT+F7 and CTRL+ALT+F8.

X :1 -ac & DISPLAY=:1 gamename

The last one may be the best one to go forth and back to the game.

---

### Post by Skywalka443 on 2007-03-03
i tried the command given and it says bash command ET (the game name) not found.

 Edit: Oh sorry i didnt see this thread was old.  :(

---


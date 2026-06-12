---
title: "Games Stuck in Top Left Corner"
date: 2007-08-06
forum: Gaming &amp; Leisure
---

### Post by DMXell on 2007-08-06
Okay, this has happened to me for many games, making them really hard to play. I'll open the game and buy default they're in windowed mode, but they won't open in the center of my screen, instead they open in the top left corner and I can't get to the bar on top of the window to move them (even by moving the Ubuntu taskbar). I'm using Compiz-fusion with a  21" widescreen monitor if that helps. Also, I tried Alt+hold and drag to see if I can drag them but Compuz macros won't work in the games so I'm stumped. Can anyone help me? Thanks!

---

### Post by atomkarinca on 2007-08-06
you can try switching windows with alt+tab or ctrl+alt+d, moving the window and switching back. that works for me. i don't if there is a setting for placing the window in the center.

---

### Post by alterpinguin on 2007-08-06
a lot of games have a console-option to enter special settings and then allow the mouse-curser to be moved out off the game-window. Next there should be an option in the windowmanager to set a default position for new progamm-windows. And last putting the game-window in the upper left corner is the right place to switch to a lower screen-resolution and have this window fill the whole computer-screen (like play the game in a 640x480 res. for old stuff).

---

### Post by DMXell on 2007-08-06
Sorry, Alt+Tab and ctrl+alt+d did nothing. 

Alterpingiun, i don't understand what you're saying...

---

### Post by atomkarinca on 2007-08-06
in a terminal or through alt+f2 type
```
winecfg
```
in the graphics tab check the first two options. that should do the trick.

---

### Post by DMXell on 2007-08-06
I'm playing native Linux games, not Wine games, Sorry, I forgot to clarify. In WIne I use a virtual desktop as it is.

---

### Post by DMXell on 2007-08-07
Can anyone help me?

---

### Post by DMXell on 2007-08-08
Bump...

---

### Post by DMXell on 2007-08-09
Bump...

---

### Post by vikrant82 on 2007-08-09
I guess, the resolution your game is trying to run at is not supported by your drivers.

For e.g. go to screen resolution, if yu dont see 640x480 then any game that runs on that resolution would take up top left area but will play as if its full screen.

Try changing ur game resolution to what ur drivers support and it would go full screen. Or other wise try to make ur driver support resolution which ur game defaultly runs on.

I face similar issue with quake 3 arena, I installed 915resolution to get lower resolutions. And that did it.

---

### Post by DMXell on 2007-08-09
My video card supports the resolution. I installed 915resoltion though and nothing happened.

---


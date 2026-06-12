---
title: "Alt-tabbing out of Urban terror"
date: 2008-10-06
forum: Gaming &amp; Leisure
---

### Post by Rotarychainsaw on 2008-10-06
OK, so when I had my nvidia card, I could alt-tab out of full screen games and the game would minimize and stop using CPU. I got a new ATI card and now I alt-tab, the screen flashes and the minimize animation kind of goes and the game sits there still going fullscreen. It looks like the mouse thinks its on the desktop, but the game is still there and I can't really do anything. 

Is there a setting in my xorg.conf maybe that would get back the normal behavior?

---

### Post by chungy on 2008-10-06
as an alternative, Urban Terror uses ioquake3, so you should be able to do an Alt-Enter to put it into windowed mode, then open the console (usually ~) to ungrab the mouse.

---

### Post by Rotarychainsaw on 2008-10-07
Nah, that doesn't work. The game is still being drawn fullscreen on the desktop, but it is still over everything else. It's really odd.

---

### Post by Sockerdrickan on 2008-10-08
It's not odd, you can blame SDL.

---

### Post by Rotarychainsaw on 2008-10-09
Darn You SDL! So why did it work OK with the Nvidia card?

---

### Post by Sockerdrickan on 2008-10-09
It's about the window management

---

### Post by Rotarychainsaw on 2008-12-22
New ATI 8.12 driver fixes this BTW. :guitar::guitar:

---

### Post by krofek on 2009-01-22
It won't work for me, none of the global keys, not in UrT nor in wine fullscreen apps. Got 8.12 ati drivers.

---

### Post by MighedOne on 2011-07-21
Try wine config => graphics => Emulate virtual desktop => enter screen size
i was able to switch to another screen that way.

---


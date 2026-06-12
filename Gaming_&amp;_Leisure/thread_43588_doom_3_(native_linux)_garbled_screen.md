---
title: "doom 3 (native linux) garbled screen"
date: 2005-06-22
forum: Gaming &amp; Leisure
---

### Post by holr on 2005-06-22
hi!

Just managed to get doom 3 up and running using the native linux installer (no cedega / wineX). However, I do geta strange problem....

My screen is set to a resolution of 1400x1050. I prefer to run doom 3 less than this as my gfx card cant keep up, but this is where it gets strange....

Whatever resolution I run doom 3 at, the screen res is still 1400x1050, its just that doom only takes up as many pixels of the screen that it is set to! E.g. 640x480 results in a small window in the bottom left corner running doom, 1024x768 results in a larger window. The rest of the viewable space is ¨garbled¨ (like the noise on a poorly tuned tv). The game is set to run fullscreen....

I did a fglrxinfo and had this:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FIREGL T2 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

Im using the ati drivers I had after doing ¨sudo apt-get install fglrx-drivers (or whatever the correct filename was)¨

I guess I could try cedega but that isnt even working for me when I try to run an old game like diablo 1!!!!

Any ideas folks? All help greatly appreciated!

**update**
Forgot to mention, im running on an ibm t41p laptop, ati firegl 2 mobility (128mbram) and running 5.04 kubuntu.

---

### Post by holr on 2005-06-23
ok, it will run fine in a window. But as my gfx card doesnt do too well with 1400x1050 res im playing in a tiny square in the middle of the desktop. Any ideas on my fullscreen woes?

---

### Post by endy on 2005-06-23
Do you have these screen modes (eg 640x480 and 1024x768 ) defined in your xorg.conf file?

That's my wild guess :)

---

### Post by holr on 2005-07-04
[QUOTE=endy]Do you have these screen modes (eg 640x480 and 1024x768 ) defined in your xorg.conf file?

That's my wild guess :)[/QUOTE]

Perfect! that did it, i only had 1400x1050 there, added "1024x768" "800x600" and "640x480" and it runs now :-) but thanks to the atis drivers, dont think i'll be playing it in anything about 640x480 for the time being!

---

### Post by SzAq on 2006-11-17
Hey I had the same problem in games like Jedi academy, Enemy Territory but in my xorg.conf resolutions are already added.

When I was on Dapper all was working fine. But now on 6.10 this resolution problem makes me sick.

---

### Post by lamda-core on 2009-03-18
I have a similiar problem. I would try the solution you suggested. But I am not sure where to start. some help?
running 8.10

---


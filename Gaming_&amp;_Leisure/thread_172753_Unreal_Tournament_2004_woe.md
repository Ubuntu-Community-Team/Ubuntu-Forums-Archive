---
title: "Unreal Tournament 2004 woe"
date: 2006-05-09
forum: Gaming &amp; Leisure
---

### Post by Wr8EYilK8Y on 2006-05-09
UT2004 runs like a dream. In fact, I can play it at 1600x1200 with no problem. EXCEPT-


The game abruptly tells me it can't find some "Engine.engine" in the configuration file if I quit and start again. Sometimes, I install it and it works, then doesn't work. ](*,) I have been unable to Google a solution

Basically, the error message is "ut2004 can't find Engine.engine in configuration file", if I recall correctly. I don't know- I'm not at home right now and can't test. And how can I get WINE to allow Unreal Tournament 1 (the Windows version) to change the resolution without leaving a corner of animation and the rest of the screen my desktop? The default resolution is 640x480, if I change it, there is a singe game windows 640x480 in teh upper left corner. The rest is my desktop, and the corner is just that- a partial of the gamescreen.


Processor-
Sempron Socket A 1.7GHz 2400+
RAM-
512MB PC3200 RAM
Video-
XFX GeForce 6200

---

### Post by Perfect Storm on 2006-05-09
You properly ran the ut2004 with root that's why it can't find it.

---

### Post by gRiMgRaVy014 on 2006-05-09
I thought I read somewhere that you shouldn't run games in root.

---

### Post by Wr8EYilK8Y on 2006-05-09
so I merely don't run Unreal Tournament in root mode? Got it- will do tonight

---

### Post by Denta on 2006-05-10
[QUOTE=Your Name Is]so I merely don't run Unreal Tournament in root mode? Got it- will do tonight[/QUOTE]
Install the game with sudo, then;

sudo chown yourusername /usr/local/games/ut2004 -R
sudo chown yourusername .ut2004 -R

---

### Post by Perfect Storm on 2006-05-10
That shouldn't be necessary.
If he makes a clean install of ut2004, sudo /blah/blah/ut2004.sh, then not press the run button after it installed but exit it and type ut2004.

---

### Post by Wr8EYilK8Y on 2006-05-10
Yeah- I hit "no" this time at the end of the GUI install. It works! THANKS GUYS!

---

### Post by Perfect Storm on 2006-05-10
^^

Seen to often with people installing games with loki installer, they forget that the end of the gui to exit to get out of sudo/su which means they don't have permissions to some files when they want to run the game next time without running sudo/su (which is a very bad idea).

---


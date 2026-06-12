---
title: "Simultaneous sounds"
date: 2006-04-21
forum: Desktop Environments
---

### Post by viciouslime on 2006-04-21
I have a game that after much reading of these forums I believe is outputting sound using OSD if that makes sense? I can't simultaneously run the game and amaroK, is there anyway to make this possible. I have finally got my system to play sound in games like planetpenguin-racer, but now i have this new problem :-k

---

### Post by louis_nichols on 2006-04-21
try starting the game with command

*aoss <game-executable>*

instead of just *game-executable*

---

### Post by viciouslime on 2006-04-21
Unfortunately I get:

bash: aoss: command not found

:(  but thanks for trying! Anything i can install to get the command to work?

---

### Post by viciouslime on 2006-04-21
Oh found it, package alsa-oss, however upon running it, the game starts but then quits and the console shows:

line 738: 15652 Segmentation fault

:( :confused:

---

### Post by louis_nichols on 2006-04-21
then... I dunno if there's smth else you can do. I remember when I was experimenting FreeBSD, there was a way to get multitasking sound under oss, but dunno how, anymore. sorry...

---

### Post by louis_nichols on 2006-04-21
look, go here:

[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/book.html#SOUND-SETUP](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/book.html#SOUND-SETUP)

and check out section 7.2.3

I don't have a linux box close, so I actually don't know wether sysctl works under Linux as described there. But it's worth trying.

---


---
title: "one emu frontend to rule them all"
date: 2008-09-28
forum: Gaming &amp; Leisure
---

### Post by klikklak on 2008-09-28
Hi all, first post here. 

How have you all handled the multiple emu problem? In the past week I've tried most/all of the various frontends available for linux:

kamefu (0.13ubuntu) works, but only recognizes my snes collection. also no support for more than gb(a/c), snes, mame. Still, if it would recognize even those, I'd be willing to use it.
gamefu (0.2beta) doesn't build. and it hasn't had a release in a year
loemu is under active development and uses gtk (unlike gamefu whcih is qt), but it only supports snes and mame and it doesn't show extras (screenshots etc)
mythgame is supports the biggest number of emus, but it doesn't show extras and seems to hang with my mame set.
wah!cade is only for mame, but very nice otherwise.
jgamebase, well I got a gamebase64 set for this, but couldn't set it up. pointing to a directory of c64 didnt do any good either. and it's java.


I'm almost willing, but not capable of adding megadrive and others to loemu, but the five line description on how to do it scared me off. How is gamebase on windows? It looks like the best supported standard around that I've seen. too bad it doesn't run on freedom.

---

### Post by ghostandmachine on 2008-09-28
what would be a better idea is to design one gui that can simply send commands to the terminal behind the scenes for all those programs.

A friend and I are actually working on such a gui in an effort to design our own game console. The gui would load and say I wanted to play MAME. I would click on the MAME button then the game and click play. So the command to do that would be sent to the terminal and the emu would load.

---

### Post by Master O on 2008-09-28
This guy has pretty good MAME and console frontends.  Now if only there were a linux port of it:

[http://www.mameworld.net/emuloader/](http://www.mameworld.net/emuloader/)

---

### Post by klikklak on 2008-09-28
ghostandmachine: That's exactly what I'm talking about, just a gui that shows relevant info and sends commands to command line emus.  Both loemu and gamefu do this, but they're limited to snes and mame (gamefu has gbX as well). 

master O:  That looks pretty good, do you know the complete list of emus he supports?

Edit: Stop the PRESS!  I just noticed that wah!cade does all I wanted and more :) Sweet, can't wait to get home to configure it

---


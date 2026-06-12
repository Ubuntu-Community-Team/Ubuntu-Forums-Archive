---
title: "Team Fortress 2 Grey screen on launch"
date: 2014-07-28
forum: Gaming &amp; Leisure
---

### Post by Guyofdoom42 on 2014-07-28
Whenever I launch Team Fortress 2 (Tf2) THe following things happen:

-Weird green bar of static on top of screen

-Actual game screen is tiny, and in top right corner, just below the bar of static

-After intro plays, the screen goes black, and I have to Alt-F4 out

-If I use the -novid parameter, I just get a dark grey screen with nothing on it

Here are my system specs:

Intel i2 processor, 64 bit

1 GB DDR2 RAM

Intel Integrated Graphics controller 82Q963/Q965

Help me out here!

---

### Post by efflandt on 2014-07-31
You would likely need more RAM (especially shared for video) and better graphics. I am not familiar with an i2 cpu, but even with i7, 8 GB RAM, and Intel HD 4600 graphics on a laptop, TF2 indicated 10 fps, but was virtually unplayable due to pauses and looping audio. Fortunately that laptop has combination graphics that also includes Nvidia GTX 765M, so once I found TF2 launch parameters to use nvidia instead of Intel graphics, it was smooth and much faster.

And older Intel graphics is worse. For 2 similar laptops from 8 or 9 years ago, both with 1.66 GHz dual core and 2.5 GB RAM, minecraft was playable on one with legacy ATI graphics (X1300 mobile), but unplayable on the other one with Intel graphics (I have not put Steam on those).

---

### Post by dunn2 on 2014-07-31
Sorry im new... but is the old team fortress 2 game??

---

### Post by oldrocker99 on 2014-07-31
Team Fortress 2 for Linux came out last year. Oddly, they don't post minimum Linux specs, but their Mac specs include,"1GB RAM, NVIDIA GeForce 8 or higher, ATI X1600 or higher, or Intel HD 3000 or higher Mouse, Keyboard, Internet Connection." Your video circuitry is below that spec, it looks like.

Googling your Intel graphics circuitry reveals a slew of problems that various distros' users report. If at all possible, increase your RAM and find a dedicated graphics card (and I strongly recommend nVidia over ATI), or many Steam for Linux games simply won't run.

You might also want a lighterweight desktop; I personally like MATE, which uses very little system RAM.

---

### Post by Guyofdoom42 on 2014-08-11
Well, I DID get it to "work" in WINE, and apparentley I need GLSL 1.3 support or something like that... Anyone know where I could find dat?

---


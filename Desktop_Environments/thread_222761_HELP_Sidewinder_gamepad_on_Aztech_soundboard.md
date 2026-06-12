---
title: "HELP: Sidewinder gamepad on Aztech soundboard"
date: 2006-07-25
forum: Desktop Environments
---

### Post by canci on 2006-07-25
hello!

I was trying to get the Sidewinder gamepad working on my
Aztech Soundboard gameport and followed the wiki on ubuntu's site,
however, I didn't know the name of the gameport module for my card :( 

The card I use loads over the snd-azt2320 alsa sound module.

So, if any1 knows what my gameport module is, PLS help me!
I lost the manual to my soundcard since it's veeeery old.

TNX! :D

---

### Post by Tsukasa on 2006-07-25
Hi, I've had a somewhat similar issue some time ago, try to do the following and see if it works:

modprobe ns558 emu10k1-gp sidewinder

Now check if you have a js0 device in /dev. If this is the case try to calibrate the gamepad (i.e. with jscalibrator). For the slight chance that the pad behaves strange (only 4 buttons displayed and/or other issues) try to
modprobe -r analog
and see what happens.

---


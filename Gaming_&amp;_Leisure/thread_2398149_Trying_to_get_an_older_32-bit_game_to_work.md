---
title: "Trying to get an older 32-bit game to work"
date: 2018-08-08
forum: Gaming &amp; Leisure
---

### Post by redvenomweb on 2018-08-08
I have an older 32-bit Linux game, Typhoon 2001.  It was released in 2007.

Since 10.04, in order to get the sound to work, I've had to install alsa-oss and start the program with ```
aoss ./typhoon
``` which has gotten the job done.  When trying to get the game to run in 64-bit Ubuntu MATE 16.04, I needed to install the following:

libgl1-mesa-glx:i386 libglu1-mesa:i386 libxcursor1:i386 libxpm-dev:i386 alsa-oss:i386

But ultimately, that worked. and I was able to run the game successfully.  However, with 64-bit (standard) Ubuntu 18.04, when I do the same thing I did in 16.04, the game takes a really long time to start and then after a while, the screen is black but I can hear the game's startup music.  If I push Esc, I can successfully exit the game, so this seems to strictly be a graphics issue.

Where should I start my troubleshooting to figure out the source of the problem?

---

### Post by Holger_Gehrke on 2018-08-08
I wouldn't have thought that there was anybody else who still played that ...

On my system (XUbuntu 18.04, Lenovo ideapad 110 AMD E2 SOC based Laptop, using the 'radeon' driver) it runs without any problem, but I can't tell you why or how I managed to get it to run -- I originally installed XUbuntu 16.10 on this machine, copied my '~/bin' directory from my old machine to this one, got typhoon working back then and it kept on working through three OS-upgrades. I didn't even need to do that 'aoss' thing you did, although there's a script I must have written on my old machine that sets LD_PRELOAD to some pulse library that doesn't exist on the new one.

Typhoon writes a log-file 'typhoon.log', this might give you some idea on what's going wrong. There's also a configuration file 'typhoon.cfg' that you could edit ...

Holger

---


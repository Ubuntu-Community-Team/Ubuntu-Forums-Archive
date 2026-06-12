---
title: "Braid, black screen then exits"
date: 2010-12-24
forum: Gaming &amp; Leisure
---

### Post by marcoskorner on 2010-12-24
Hi everyone¡
The problem is when I try to start braid, it comes out a black screen, nothing happens and then returns to the desktop without showing any error in the terminal (There is no error on the console, just 0 when i use ./braid -windowed ; echo $?)

I believe its what happens in Icculus Bugzilla Bug 4830 , I already did whatever they post in that page ([http://bugzilla.icculus.org/show_bug.cgi?id=4830](http://bugzilla.icculus.org/show_bug.cgi?id=4830)), but nothing worked, I also have a GeForce FX5200 with latest installed drivers.

I first thought it was the "S3TC" problem some other gamers get but it is not the same error message. Anyway, i tried to run driconf and get an alert saying "XDriInfo returned with non-zero exit code." and an error message in the terminal: "libGL is too old."

This is what i have done to fix it (without getting to make it work):
Switch Nvidia drivers
Delete the library files (libstdc++, libgcc_s, and libSDL) taha come with the game
Start with all the options -windowed, -no_post, -language, etc
Using the new build (braid-linux-build2.run.bin)


So I found a way to make it work but its far form perfect:

I change nvidia drivers and i can play without restarting, that means I can play without Direct render, but when I restart and the drivers are fully functional with direct render, the problem comes again, so i have to disable drivers for the game to work in low resolution and kind of slowly.

Any thoughts o suggestions???

---


---
title: "Mesa/X without DRI performs better than with DRI on SiS"
date: 2006-08-19
forum: Desktop Environments
---

### Post by brkamikaze on 2006-08-19
I am a user of a SiS video card and I noticed on a LFS system that when I explicitly "forbid" Mesa and X to compile without DRI, all the OpenGL demos run faster than with the (unsupported) DRI support. For example, when I used Fedora, glxgears printed 200fps+ on the console but on the screen it looked more like 0.5 fps. Now, on the LFS system, it runs smoothly.

I'd like to know if there is a option or a package for me to install X server and Mesa without DRI; or if there is a configuration that achieves this same thing. I am using the vanilla "X -configure" file modified only to use the resolution I want and the keyboard layout I own.

If I need to compile the package myself, I'd like to know how to integrate with dpkg and to make apt only upgrade it if it is explicitly listed. I'd also like to know how to pass my cool CFLAGS to the deb build system :)

Notice: I compiled everything with a kinda "absurd" CFLAGS, but it worked: "-O3 -pipe -fomit-frame-pointer -march=athlon-xp -mtune=athlon-xp -mmmx -m3dnow -msse"

---

### Post by brkamikaze on 2006-08-19
Tried to do a "benchmark" (if glxgears is such a thing) on the Desktop CD. Runs terribly, and doesn't print those fps lines.

---


---
title: "wxWidgets and OpenGL"
date: 2006-11-11
forum: Desktop Environments
---

### Post by howipepper on 2006-11-11
I'm not sure if this is the correct forum to post this question in, but if not, could the moderator please move it to the correct thread?

Anyway, my question concerns OpenGL with wxWidgets on 6.10.  I have all of the latest wxWidgets (and wxGTK) packages from the Ubuntu archives installed on my system.  I've compiled some of the wxWidgets example programs with no problem, but when I tried to build one of the OpenGL samples, I received the following error:

/usr/bin/ld: cannot find -lwx_gtk_gl

I looked at the wxWidgets packages in the archives, but couldn't find anything that might lead me to the correct answer.  I'd like to find and install this missing wxWidget library so I can compile the samples.

For more info, I'm running a Dell Dimension E520 with a 2.66 GHz Pentium D processor, 1 GB of RAM and an ATi Radeon X1300 Pro video card, running the latest ATi driver from their web site.

Any assistance would be greatly appreciated!

---

### Post by pixienick on 2008-02-18
have you compiled the wxWidgets library with the opengl flag? - this does not happen by default. Took me awhile to get this opengl in wx. I guess you know to compile your program with the gl flags like ;
g++ OpenglApp.cpp `wx-config --cflags` `wx-config --gl-libs`

---


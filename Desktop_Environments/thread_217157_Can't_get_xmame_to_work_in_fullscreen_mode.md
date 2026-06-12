---
title: "Can't get xmame to work in fullscreen mode"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Flutterby on 2006-07-16
Hello,

I have installed the package xmame-x.  When I start it I always get these mesages:

> GLERROR: cannot access OpenGL library libGL.so
GLERROR: dlerror() returns [libGL.so: cannot open shared object file: No such file or directory]
Use of OpenGL mode disabled
XDGAOpenFramebuffer failed
Use of DGA-modes is disabled

As a result of this (I presume) I am unable to play mame games in full screen mode.

Can anybody help me here?

---

### Post by r3dux on 2006-08-18
flutterby,

I was having the same issue, and fixed it by going "locate libGLU" in the console, and there was a "libGLU.so.1" and "libGLU.so.1.3.060501" file (the latter being the most recent time-stamped file).

As I didn't know where to change the fact that xmame was looking for "libGLU.so", I just ran:

sudo ln -s /usr/lib/libGLU.so.1.3.060501 /usr/lib/libGLU.so 

to make a symbolic link from the latest file I had, to the filename xmame was looking for (i.e., libGLU.so) - so if you do the same from whatever's the latest version of libGLU.so.<whatever> on your box, I'd imagine it would work for you too! (If you don't have any versions of libGLU just search for it in the adept package manager and install some GLU stuff).

[BTW I'm in no way any kind of linux expert, and there's prolly a better way to solve this problem, but this worked for me!]

Best wishes,
r3dux

---

### Post by .lobo on 2007-08-27
Hi Chaps,

Old thread - but found a solution, you don't need the libGLU.so symlink.

add the following lines to /etc/xmame/xmamerc

video-mode   1
fullscreen      1

while you're at it you could change skip_disclaimer & skip_gameinfo to 1 to skip those initial messages and get straight to the action.

The above worked for me, happy gaming!

---


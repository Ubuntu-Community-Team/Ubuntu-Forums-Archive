---
title: "Black opengl window"
date: 2005-03-25
forum: Desktop Environments
---

### Post by EddieX on 2005-03-25
Hi.
I have been using Ubuntu now for a couple of weeks and im really satisfied with it.

I can play games like quake3, enemy-territory without any problems at all.
But when i try to run opengl apps like the examples from nehe.gamedev.net i only get a black window.

I have searched the web + forums and i cant find anything about it.

Im using the Nvidia glx etc, and it works just fine, have also commented out dri in my x config and same result. So now im out of ideas :)

anyone?

---

### Post by straver on 2005-04-02
I also have this problem. It occurs when I compile an opengl-app with g++ (gcc produces working apps).

I've tried with g++-3.3 and g++-3.4. g++-3.4 gives me this warning:

> /usr/bin/ld: warning: libstdc++.so.5, needed by /usr/lib/gcc/i486-linux/3.4.4/../../../../lib/libGLU.so, may conflict with libstdc++.so.6

---


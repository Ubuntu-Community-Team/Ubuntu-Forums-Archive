---
title: "Bug: Yellow frames getting stuck in Unity"
date: 2012-01-08
forum: Desktop Environments
---

### Post by skagedal on 2012-01-08
Hi!

I'm having some troubles with big yellowy frames getting stuck on the desktop; see attached image.

I was told on IRC that this is a known bug and that it will be fixed in 12.04. Great! But is there anything I can do about it right now? It's quite annoying. 

I haven't been able to find any information by googling and searching in the forum, I guess I don't quite know what to look for. Happy to get any pointers. 

I'm running a freshly installed Ubuntu 11.10 on a Fujitsu Siemens laptop. (I guess this is "Unity" I'm running and not Unity 2D? How do I check this?)

Regards,
Simon

---

### Post by LinuxFan999 on 2012-01-08
There are only 2 solutions I can think of:
 
1. Use Unity 2D.
 
2. Use a different desktop environment, like KDE, XFCE, and LXDE.
 
It looks as if you are running Unity 3D, but you can check by running "unity_support_test -p" in the terminal. If it says yes to everything, then you are using Unity 3D.

---

### Post by skagedal on 2012-01-08
Thank you! Yes, indeed it seems to be Unity 3D:

> 
simon@zebra:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM x86/MMX/SSE2
OpenGL version string:  1.4 Mesa 7.11

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes


I will have a go then at trying Unity 2D or possibly some other desktop environment, if there are no other solutions! Happy the way Unity 3D works otherwise, though...

Regard, Simon

---


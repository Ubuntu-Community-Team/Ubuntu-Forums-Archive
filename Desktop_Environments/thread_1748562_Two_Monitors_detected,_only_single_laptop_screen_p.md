---
title: "Two Monitors detected, only single laptop screen present."
date: 2011-05-03
forum: Desktop Environments
---

### Post by zonky on 2011-05-03
Hi, I have a notebook where it appears a fresh install of natty has detected 2 screens as being present, and set them to be mirrored.

However, there is only one screen present.

It's a Hp 5320m, with a Intel HD graphics.

Here's what the unity test says:

~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile GEM 20100330 DEVELOPMENT 
OpenGL version string:  2.1 Mesa 7.10.2

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

Unity supported:          yes

Here is what i see in monitors when i uncheck 'mirrored'

[http://img97.imageshack.us/img97/1461/screenshothw.png](http://img97.imageshack.us/img97/1461/screenshothw.png)

If i disable either of these two monitors, then i lose the screen for both- oops.

Really don't know how to troubleshoot this, appreciate anyhelp!

---

### Post by zonky on 2011-05-03
While the above is weird, the end goal is to attach an external monitor via my hp displayport- no end of trouble trying to re-configure this currently.

---

### Post by zonky on 2011-05-03
Makes no difference if i use the VGA connector- still end up with 3 different monitors, none of which are configurable :(

Is there anyway to force re-detection of my graphics hardware?

---

### Post by zonky on 2011-05-03
Just managed to find this bug assigned:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773734](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773734)

---


---
title: "the 3d version won't start"
date: 2011-10-15
forum: Desktop Environments
---

### Post by momchil9 on 2011-10-15
hey, ive stumbled upon this problem after updating from 11.04 to 11.10:

when i log in with ubuntu default it just starts logging-in and gets me to a blank desktop. got no problem with unity-2d, had no problem on 11.04. i run with nvidia 6600gt with the recommended driver.

sorry for the text formating, typing with onboard and a mouse :(

---

### Post by 23dornot23d on 2011-10-15
Check that the Nvidia Driver has loaded up


nvidia-settings should work if it has

---

### Post by momchil9 on 2011-10-15
nvidia x server settings is running.

edit: yeah, ill paste that too:

```
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

```

---

### Post by Simeo on 2011-10-15
I'm having the same issue, only with an ATI driver. Unity 2D is working, but once I try 3D I just get a blank desktop. I need to press my power button to shutdown and I can't even get a terminal to load with ctrl+alt+T....

I'm having a similar issue, but I have an ATI Graphics Card.

My output of /usr/lib/nux/unity_support_test -p in Unity 2D is:

```
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string:  3.3.11005 Compatibility Profile Context

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
```

:confused:

---

### Post by momchil9 on 2011-10-17
any ideas someone?

---

### Post by Simeo on 2011-10-17
> **momchil9 said:**
> any ideas someone?

My version was upgraded from 11.04. I ended up installing another instance of 11.10 as a 'clean install' in a separate partition, then transferred files from the original partition into the clean partition. Now my Gnome3 and Unity 3D work.

---


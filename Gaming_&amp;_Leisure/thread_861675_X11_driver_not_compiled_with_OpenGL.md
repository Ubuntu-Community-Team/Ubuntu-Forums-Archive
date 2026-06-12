---
title: "X11 driver not compiled with OpenGL?"
date: 2008-07-16
forum: Gaming &amp; Leisure
---

### Post by imaligertamer on 2008-07-16
This problem is really annoying me. After installing AlephOne, none of the games on my computer that require OpenGL will run. After trying to run them from the terminal, I get this message:

[INDENT]byron@byron-laptop:~$ sauerbraten
Using home directory: /home/byron/.sauerbraten
init: sdl
init: enet
init: video: mode
Unable to create OpenGL screen: X11 driver not configured with OpenGL
byron@byron-laptop:~$ 
[/INDENT]

I found another thread with a problem similar to this, but the solutions presented did not work for me. I'm running Hardy on a Dell Inspiron 6400 series with a Nvidia GeForce 7900. Any help would be appreciated.

---

### Post by kdorf on 2008-07-16
You're probably not running the restricted drivers.

You need to install the official NVIDIA drivers from the site (guides all over on how to do that in Ubuntu) or install the drivers a la
```
sudo apt-get install nvidia-glx-new
```

The latter is much easier.

---

### Post by imaligertamer on 2008-07-18
I've already done that.

---

### Post by imaligertamer on 2008-07-21
Help? (A bump, to be honest)

---

### Post by DoktorSeven on 2008-07-21
Did you check any HOWTOs on the subject? e.g. [Ubuntu docs](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)?  Best thing is to run the hardware driver manager and reboot after install.  Read some of the Troubleshooting if you still have a problem (and know that any fix you make will require restarting).

The ultimate test is to type this into a terminal:

```
glxinfo | grep direct
```
You should get back "direct rendering: Yes".

---

### Post by jvin248 on 2008-08-06
problems too running OpenGL...

Video Card Nvidia NV20 Geforce3 pci, Xubuntu 8.04 (fresh install yesterday).

Installed the Nvidia-restricted-drivers, then nvidia-glx-new, mesa-utils.
"glxinfo" shows

Xlib: extension "GLX" missing on display "0.0"

errors running Sauerbraten (2008_06_20_ctf_edition)

"init: sdl
init: enet
init: video: mode
Unable to create OpenGL screen: Couldn't find matching GLX visual"

---


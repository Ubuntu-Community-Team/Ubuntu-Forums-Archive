---
title: "Open Arena OpenGL subsystem"
date: 2007-11-10
forum: Gaming &amp; Leisure
---

### Post by Crimmy on 2007-11-10
I'm a n00b to anything Linux, and I'm trying to learn so bear with me, please! ;)

I used Add/Remove Applications and thought I'd try Open Arena but after tying "openarena" in Terminal, I get a OpenGL Subsystem error:
[B]
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem[/B]

My computer specs are: 

Ubuntu 7.10
Kernel Linux 2.6.22-14-generic
Gnome 2.20.0
Memory: 512MB
Dual P4 3.20GHz
G72 GeForce 7300 LE 

How can I find out that I'm using the correct driver for my GeForce 7300?  I would imagine that it supports OpenGL.  How can i check for sure?

---

### Post by hikaricore on 2007-11-10
Here's a couple things to test.

```
glxinfo | grep rendering
```

This should return yes^

```
cat /etc/X11/xorg.conf | grep Driver
```

You should see one line list: nvidia

If you see "nv" search around the forums for Nvidia driver installation guides, there's tons of them.

---

### Post by Crimmy on 2007-11-10
Thanks for the help! I tried the code and got the following:

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

Also tried the other code and got:

```

        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "nv"
```

Having the hardest time making sure that the latest Nvidia drivers are installed. *sigh...  time to go searching again!

Thanks for your help, hikaricore

---

### Post by anjilslaire on 2007-11-10
I see you're running Ubuntu 7.10, so this'll be easy:
Use the Restricted Driver Manager, and enable the video driver for your card. It'll configure everything for you, pretty much.

---

### Post by Crimmy on 2007-11-12
Hey that seemed to work great! Thanks a bunch, anjilslaire.

And thanks to you, hikaricore for the way to test the card through terminal!

I'm off to play a bit of OA now. :D

---

### Post by hikaricore on 2007-11-12
Glad to be of help.  ^_^

Happy fragging.

---


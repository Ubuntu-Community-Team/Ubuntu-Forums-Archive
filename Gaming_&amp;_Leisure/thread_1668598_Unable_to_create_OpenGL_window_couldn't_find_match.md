---
title: "Unable to create OpenGL window: couldn't find matching GLX visual"
date: 2011-01-16
forum: Gaming &amp; Leisure
---

### Post by Odexios on 2011-01-16
I recently installed Ubuntu 10.10 on an asus netbook, and everything has  worked fine until a few days ago. I used to play Uplink, naev and a few  other games in my spare time, but when I tried yesterday to launch some  of them I've got (in various forms) this error:

```
Unable to create OpenGL window: couldn't find matching GLX visual
```

This, for instance, is the message naev gives me:

```
giovanni@giovanni-1015P:~$ naev
 NAEV v0.4.2
 Sea of Darkness

SDL: 1.2.14 [compiled: 1.2.14]

Available fullscreen modes:
  1024 x 600
  800 x 600
  640 x 480
ERROR opengl.c:448 [gl_createWindow]: Unable to create OpenGL window: Couldn't find matching GLX visual
NAEV recieved SIGABRT!
./naev() [0x808a4e5] loadscreen_render(...):0 ??
[0xc1c40c] ??(...):0 ??
/lib/libc.so.6(abort+0x182) [0xde2e42] ??(...):0 ??
./naev(gl_init+0xa64) [0x8099304] gl_init(...):0 ??
./naev(main+0x2ec) [0x808aafc] main(...):0 ??
/lib/libc.so.6(__libc_start_main+0xe7) [0xdcbce7] ??(...):0 ??
./naev() [0x8059321] _start(...):0 ??
Report this to project maintainer with the backtrace.

```

I googled the error a bit, and I've seen it was a quite common problem a  while ago, but I couldn't really find a solution. Is there anyone who  can help me figure out what's wrong?

---

### Post by Technophobia on 2011-01-16
What kind of graphics card? How did you install the graphics drivers? Can you run "glxgears" from the terminal?

---

### Post by Odexios on 2011-01-16
> **Technophobia said:**
> What kind of graphics card? How did you install the graphics drivers? Can you run "glxgears" from the terminal?
I have an integratedIntel GMA 950 chipset. I didn't install any driver, everything worked (for a while, at least) out of the box.

This is the output from glxgears:

```
giovanni@giovanni-1015P:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

---

### Post by Odexios on 2011-01-16
> **Technophobia said:**
> What kind of graphics card? How did you install the graphics drivers? Can you run "glxgears" from the terminal?
I have an integratedIntel GMA 950 chipset. I didn't install any driver, everything worked (for a while, at least) out of the box.

This is the output from glxgears:

```
giovanni@giovanni-1015P:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

---

### Post by Odexios on 2011-01-16
> **Technophobia said:**
> What kind of graphics card? How did you install the graphics drivers? Can you run "glxgears" from the terminal?
I have an integratedIntel GMA 950 chipset. I didn't install any driver, everything worked (for a while, at least) out of the box.

This is the output from glxgears:

```
giovanni@giovanni-1015P:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

---

### Post by Odexios on 2011-01-16
> **Technophobia said:**
> What kind of graphics card? How did you install the graphics drivers? Can you run "glxgears" from the terminal?
I have an integratedIntel GMA 950 chipset. I didn't install any driver, everything worked (for a while, at least) out of the box.

This is the output from glxgears:

```
giovanni@giovanni-1015P:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

---

### Post by Odexios on 2011-01-16
> **Technophobia said:**
> What kind of graphics card? How did you install the graphics drivers? Can you run "glxgears" from the terminal?
I have an integratedIntel GMA 950 chipset. I didn't install any driver, everything worked (for a while, at least) out of the box.

This is the output from glxgears:

```
giovanni@giovanni-1015P:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

EDIT: Sorry for the multi-multi-[...]multi post, guys. It seems I had some connection issues. Is there a way to delete the previous posts?

---

### Post by Technophobia on 2011-01-16
Try to reinstall/install the Intel graphics driver. I don't have any experience with Intel GPUs so good luck with your google fu.

---


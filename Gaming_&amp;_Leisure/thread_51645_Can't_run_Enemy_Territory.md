---
title: "Can't run Enemy Territory"
date: 2005-07-24
forum: Gaming &amp; Leisure
---

### Post by USAOwnz on 2005-07-24
Here is what I get with the glxgears
root@ubuntu:/home/usaownz # glxgears
5520 frames in 5.0 seconds = 1104.000 FPS
6554 frames in 5.0 seconds = 1310.800 FPS
6543 frames in 5.0 seconds = 1308.600 FPS
6720 frames in 5.0 seconds = 1344.000 FPS
6577 frames in 5.0 seconds = 1315.400 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
root@ubuntu:/home/usaownz #

And that is how it looks like when I try to run it, just goes black. Nothing else.

---

### Post by charlieg on 2005-07-24
Have you tried running it from a console (aka terminal)?  If not, do so.  What does it say?

---

### Post by USAOwnz on 2005-07-24
It runs, but when it does it covers up the terminal. It starts up but it is not on FULL screen. What it does is just stay black.

---

### Post by charlieg on 2005-07-24
Move the terminal so that you can focus it, and after waiting a while for ET to do whatever it is it's doing, focus the terminal (alt-tab?) and ctrl-c (auto-kills it).

---

### Post by USAOwnz on 2005-07-24
Well, it does not even show the terminal, doesn't even have a little bar think on the workspace bar. It is just a black square that "zoomed in" my whole desktop.

---

### Post by charlieg on 2005-07-25
Load a terminal (Applications -> System Tools -> Terminal), move it to somewhere it won't get covered and type 'et' in to launch Enemy Territory.  And then report back with the produced log of information!

---

### Post by pailhead on 2005-07-25
[QUOTE=charlieg]Load a terminal (Applications -> System Tools -> Terminal), move it to somewhere it won't get covered and type 'et' in to launch Enemy Territory.  And then report back with the produced log of information![/QUOTE]
 I'm having the same issue after getting my nvidia drivers to work.. (course I haven't rebooted so I don't know if it will stay when I return <G>) 

Here's my terminal screen after killing ET.

```

3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce4 Ti 4400/AGP/SSE/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 Ti 4400/AGP/SSE/3DNOW!
GL_VERSION: 1.5.3 NVIDIA 71.74

```

Deleted stuff from the screen...

```

GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
Received signal 2, exiting...

```

Any ideas? I'm running my desktop at 1600x1200, so I can't get in to set the res of ET yet.

---

### Post by Gnobody on 2005-07-25
Type: killall -9 esd before running it.  See if that works

Also, what video card do you have? Your GLX gears score seems a bit low.

---

### Post by USAOwnz on 2005-07-25
Geforce 4 MX, but am going. However, I just bought a x600 xt and a AMD 64 Venice +3000 along with a DFI Nforce 4 board that I will soon have up and running.

---

### Post by Gnobody on 2005-07-25
[QUOTE=USAOwnz]Geforce 4 MX, but am going. However, I just bought a x600 xt and a AMD 64 Venice +3000 along with a DFI Nforce 4 board that I will soon have up and running.[/QUOTE]
 ATi's support for Linux really blows but I imagine with that card you will still see 4500 in GLX gears.

---

### Post by pailhead on 2005-07-26
I'm running a Ti4400 on my nvidia box. Which is here at work :)

If anyone has an idea how to get past the black box issue let's hear it :)

---

### Post by USAOwnz on 2005-07-27
[QUOTE=pailhead]
If anyone has an idea how to get past the black box issue let's here it :)[/QUOTE]I concur.

---

### Post by USAOwnz on 2005-07-27
We oughta make a howto install Enemy Territory in Hoary.

---


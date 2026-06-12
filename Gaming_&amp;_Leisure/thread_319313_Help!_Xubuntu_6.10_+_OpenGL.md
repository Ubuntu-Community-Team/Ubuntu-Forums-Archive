---
title: "Help! Xubuntu 6.10 + OpenGL"
date: 2006-12-15
forum: Gaming &amp; Leisure
---

### Post by lorota on 2006-12-15
Hello this is my first post here, and im with some problems wiht opengl!

My first step was install the nvidia drivers for my xubuntu, and it was sucefull... the nvidia logo show on the screen when the x start...

The problem come when i will play some opengl game, like quake 3...

Here is my glxinfo:

name of display: :0.0
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

Now my glxgears:

Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

Now when tried to start quake 3, just see a black screen and fall back to the terminal:

----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

So, how can i fix this problem with the opengl??

ps: i have a TNT2 mod64, sorry my bad english!!!

---

### Post by angryfirelord on 2006-12-15
The TNT is some old nvidia card so it probably doesn't have any OpenGL support in it. You could try to do a sudo dpkg-reconfigure xserver-xorg and when you get to the list of extensions, enable the glx box.

---

### Post by jbtito03 on 2006-12-15
Hi

No, it supports OpenGL. 

First make shure you have the nvidia-legacy drivers and the legacy kernel modules.

Please post your xorg.conf and xorg.0.log :D

I can tell you that i had to disable the composite extension in the xorg.conf

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

Well... if you need further help contact me thru private msg.

Cheers

JB

---

### Post by xenoalien on 2006-12-25
I have the same error and I need it fixed ASAP.

---

### Post by xenoalien on 2006-12-25
I can't get any 3D things to run and it is making me mad. :evil: ](*,) :evil: ](*,)

---


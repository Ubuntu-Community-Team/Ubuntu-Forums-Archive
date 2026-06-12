---
title: "DRI working, but Q3A doesn't seem to see it"
date: 2006-04-21
forum: Gaming &amp; Leisure
---

### Post by charnooh on 2006-04-21
Hello!
I struggled a bit to finally get Quake 3 Arena and Direct Rendering working, and they both are... but unfortunately not together...

glxinfo shows this:
> 
sos@sos:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: Yes**
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions: [blah blah blah]
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions: [blah blah blah]
OpenGL vendor string: Keith Whitwell
[B]OpenGL renderer string: Mesa DRI i810E 20050818 x86/MMX/SSE
OpenGL version string: 1.2 Mesa 6.3.2[/B]
OpenGL extensions: [blah blah blah]    
glu version: 1.3
glu extensions: [blah]

and when i run quake 3 (by the way it's demo...)it shows this (it's just a part):

> 
----- R_Init -----
...loading libGL.so: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found

GL_VENDOR: Mesa project: [www.mesa3d.org](www.mesa3d.org)
**GL_RENDERER: Mesa GLX Indirect**
GL_VERSION: 1.2 (1.5 Mesa 6.2.1)
GL_EXTENSIONS: [blah blah]


And glxgears does this:
> 
sos@sos:~$ glxgears -printfps
1717 frames in 5.0 seconds = 343.315 FPS
1700 frames in 5.0 seconds = 339.855 FPS
1698 frames in 5.0 seconds = 339.497 FPS
1687 frames in 5.0 seconds = 337.365 FPS
1706 frames in 5.0 seconds = 341.168 FPS


I have no idea what to do to enable Quake using DRI. I browsed half of the internet, and I've found nothing helpful...

---


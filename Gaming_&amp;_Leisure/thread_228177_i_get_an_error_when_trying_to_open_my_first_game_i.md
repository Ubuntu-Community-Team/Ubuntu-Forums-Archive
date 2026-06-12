---
title: "i get an error when trying to open my first game i installed i need help badly"
date: 2006-08-02
forum: Gaming &amp; Leisure
---

### Post by kingvicious on 2006-08-02
well first off iam a linux noob so plz bare with me. i would of posted this in the begginers section but since its a game issue i thought it was best suited in this area but anyways i followed a ubuntu guide to install wolfenstein enemy territory and when i open the program in the terminal or just through application/other/enemy-territory i get this in my terminal 


ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/kingvicious/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem



even though iam noob and have no experince in this kind of thing i can still tell that iam missing something iam just 100 percent sure what i need to get here. plz help me out i cant go much longer without fragging on et XP

---

### Post by Footissimo on 2006-08-02
type into a terminal```
glxinfo | grep direct
```

---

### Post by kingvicious on 2006-08-02
i did and i get this 


Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by Footissimo on 2006-08-02
Hmm

Have you installed your graphics drivers?  If so then they don't seem to be working..search in the [Wiki](https://wiki.ubuntu.com/Home?action=show&redirect=FrontPage)

---

### Post by kingvicious on 2006-08-02
well i know i did a ubuntu guide for my nvida driver but i must of done it wrong XP

---

### Post by kingvicious on 2006-08-02
i understand now stupid me must not of going through the whole nvidia drivers installtion well thank you very much for your help man iam still setting it up so hopefully this fixes it :P

---

### Post by Footissimo on 2006-08-02
Nvidia should be fairly easy...off the top of my head:

```
sudo apt-get install nvidia-glx
sudo apt-get install nividia-glx-config enable
```

Reboot and then try the game again - if it comes up with the same errors then :

```
sudo gedit /etc/X11/xorg.conf
```

Then copy and paste the resulting text editor screen here :)

Ah..just seen your last post..good luck!

---


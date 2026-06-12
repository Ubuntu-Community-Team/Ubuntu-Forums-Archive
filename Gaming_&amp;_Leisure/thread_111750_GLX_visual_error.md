---
title: "GLX visual error?"
date: 2006-01-02
forum: Gaming &amp; Leisure
---

### Post by ren wins on 2006-01-02
when i try to run armagetron, i get this error
> 
laserwolf@violet:~$ armagetron
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual
Error in bool sr_InitDisplay() in ../../../src/render/rScreen.cpp:566 :

Sorry, played all my cards trying to initialize your video system.
Armagetron won't run on your computer. Reason:

Couldn't set video mode: Couldn't find matching GLX visual

I'll try again from the beginning, but the chances of success are minimal.

Fatal signal: Segmentation Fault (SDL Parachute Deployed)
*** glibc detected *** corrupted double-linked list: 0xb7cd4938 ***
Aborted

i've installed the nvidia-glx and glx-dev packages through synaptic
i dont, however, see an nVidia logo when i startup, and i dont think i've removed it by editing that whats-it file

i get a similar error when i try to run warsow

help please?

---

### Post by Perfect Storm on 2006-01-03
Seems that you forgot to enable (not the same as install) 3D acc.

write:
```
sudo nvidia-glx-config enable
```
in the terminal and reboot.

If it doesn't help. Then:

```
sudo gedit /etc/X11/xorg.conf
```

Find **Section Device**, under it change **Driver      "nv"** to **Driver        "nvidia" **

Also check the **Section Module** if you have the line that says: **Load	"glx"**


reboot.

---


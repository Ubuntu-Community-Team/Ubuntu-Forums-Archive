---
title: "3D Acceleration on Xpress 200M"
date: 2006-09-25
forum: Desktop Environments
---

### Post by TrsHunt on 2006-09-25
I am running the latest version of Ubuntu on a Compaq Presario v2000z. I tried getting hardware acceleration to work using this guide: 

[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557) 

It didn't work. When I run fglrxinfo, this is the output I get:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

This is what my xorg.conf looks like:

[http://pastebin.ca/182463](http://pastebin.ca/182463)

Here are some other outputs that might help out:

$ grep DRI /var/log/Xorg.0.log

(II) Loading extension XFree86-DRI
(==) fglrx(0): NoDRI = NO
(WW) fglrx(0): * DRI initialization failed!                  *
(EE) AIGLX: Screen 0 is not DRI capable



$ lsmod | grep fglrx

fglrx                 407372  0 
agpgart                35144  2 fglrx,ati_agp



Please help me out guys, thanks.

---


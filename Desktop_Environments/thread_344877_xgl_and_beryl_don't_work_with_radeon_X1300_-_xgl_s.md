---
title: "xgl and beryl don't work with radeon X1300 - xgl session freezes on startup"
date: 2007-01-23
forum: Desktop Environments
---

### Post by jsb56 on 2007-01-23
I'm very new to linux, but have installed edgy on my dell E521 computer with a raedon x1300 pro 256Mb graphics card. I have installed fglrx and got the card working (in that glxgears work). 

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Generic
OpenGL version string: 2.0.6011 (8.28.8 )

I have tried to install beryl and xgl using the guide at [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

But when I try to login to an xgl session the desktop freezes. If I select Beryl as the window manager in a gnome session is falls straight back to gnome.

Any ideas?

---

### Post by makajawanjack on 2007-02-10
I have the same problem, with an ATI Mobility X1300. glxgears gives me ~700 fps, but beryl won't work because it says direct rendering isn't enabled. Help here would be greatly appreciated.

---

### Post by makajawanjack on 2007-02-10
My fglrxinfo gives me this:
> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

---

### Post by arnoldXXX on 2007-03-14
I Have the same problem... Setup: amd64 x800xl pci-e.
But i also have the freeze problem when i try to log out, shut down, restart etc. might bee the problem (who knows) fu*k ati!

---

### Post by jbernardo on 2007-04-30
I'm having lots of freezes with xgl/fglrx on a laptop with a radeon xpress 200M chipset. For now, I'm using plain xorg with kde (direct rendering is enabled thanks to fglrx).

---

### Post by jaynes on 2007-05-07
Hey, jsb56,

It sounds like I have the same Dell setup as you do. I have not yet been able to get my video working properly. I can't get the widescreen resolution that my monitor can display. I've tried a lot of the how-to suggestions but nothing has worked for me.

I would really appreciate if you could please explain the steps you took to get your video working.

Thanks, Will

---


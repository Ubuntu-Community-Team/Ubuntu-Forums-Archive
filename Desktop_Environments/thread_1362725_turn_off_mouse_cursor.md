---
title: "turn off mouse cursor"
date: 2009-12-23
forum: Desktop Environments
---

### Post by gushy on 2009-12-23
Can anyone tell me how I can disable the mouse cursor in x.org?

I have a media pc (xbmc) that I only use the remote and keyboard on (although the keyboard receiver has mouse support, and a mouse I don't use it) and I want to stop the cursor appearing.

Initially the mouse cursor is hidden, but if I resume from suspend the cursor appears in the middle of the screen and only goes away with a reboot.

I'm running 9.04 with nvidia drivers.

---

### Post by hariks0 on 2009-12-23
There is an applet to lock mouse in to it. It is available in 9.04 not in 9.10.

---

### Post by gushy on 2009-12-23
I have seen that, however I'm not using gnome so I'm not sure it's any use to me in this instance (used it for a while on my work system, it can be quite handy).

In this instance I'm loading X with no window manager, and launching xbmc from .xsession

---

### Post by vdr60 on 2009-12-23
I suppose it is a bug. Try to monitor this:
[http://xbmc.org/trac/ticket/5362](http://xbmc.org/trac/ticket/5362)

---

### Post by gushy on 2009-12-23
I believe that is related to the issue I'm seeing, and I saw someone say that they think it's to do with SDL not knowing how to handle the mouse properly when coming out of suspend.

That makes sende to me Fixing that is fine if you want to keep and use the mouse.  

However I don't want to use the mouse ever and I figured there might be an xorg.conf switch I don't know about (or maybe an nvidia driver option) that would allow turning off of the mouse cursor at the x window level rather than the application level.

---

### Post by vdr60 on 2009-12-23
This is describing a way to have a dummy mouse in xorg.conf
[http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html)

It is for a touch screen, I don't know if it make dummy also your keyboard....

In any case here is a detailed explanation on xorg.conf parameters:
[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

---

### Post by gushy on 2009-12-23
ooh that's interesting, I'll give that a try.

---


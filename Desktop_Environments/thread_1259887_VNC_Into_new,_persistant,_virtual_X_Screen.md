---
title: "VNC Into new, persistant, virtual X Screen"
date: 2009-09-06
forum: Desktop Environments
---

### Post by nolanpro on 2009-09-06
I've successfully got x11vnc running so I can control the monitor that is physically connected to my machine.

What I need to do now, is VNC into a separate virtual x screen, that will give me a real desktop thru VNC, with no such hardware attached. I would prefer to specify the geometry so the x screen fits within it's window on my laptop screen.

I've seen a lot of info on xvnc (as opposed to x11vnc). However, the info is old, vnc4 is buggy, and and very last posts seem to suggest its not working on 9.04 (my dist) anyway.

So I'm hoping there's maybe something new out there. I still want to VNC into my physical desktop (5900) but I want a new desktop, that's always running, and that I can VNC into (5901).

Any ideas? Thanks!!!

---

### Post by MountainX on 2009-09-07
I don't really know what you're asking, but I think you might be looking for something like NoMachine NX Free (or [FreeNX]("http://freenx.berlios.de/"))

---

### Post by krunge on 2009-09-07
> **nolanpro said:**
> 
I've seen a lot of info on xvnc (as opposed to x11vnc). However, the info is old, vnc4 is buggy, and and very last posts seem to suggest its not working on 9.04 (my dist) anyway.

If the package 'vnc4server' is not working for your system, perhaps the 'tightvncserver' package is still working.
> 
So I'm hoping there's maybe something new out there. I still want to VNC into my physical desktop (5900) but I want a new desktop, that's always running, and that I can VNC into (5901).
If 'tightvncserver :1' doesn't work you can actually also do virtual desktops with x11vnc.  Just add the 'xvfb' package (sudo apt-get install xvfb) and run something like this:```
x11vnc -rfbport 5901 -create
```However this mode may take some tweaking to get working the way you want; and of course it will be a bit slower than tightvncserver.

---

### Post by nolanpro on 2009-09-07
By Golly krunge, that's exactly what I was looking for! I've never ever heard of tightvncserver, but it works like a charm.

A little tweaking and i'm sure i'll get it exactly how I need it. The output of running tightvncserver basically sums up my original post "New 'X' desktop is server:1"

Thanks again!

---

### Post by krunge on 2009-09-07
> **nolanpro said:**
> By Golly krunge, that's exactly what I was looking for! I've never ever heard of tightvncserver, but it works like a charm.
TightVNC server is just a fork of the RealVNC server (which is evidently not working on your system.)
[INDENT][http://www.tightvnc.com/](http://www.tightvnc.com/)[/INDENT]

---


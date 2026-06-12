---
title: "Xnest Session with fglrx enabled DRI (under XGL)"
date: 2006-07-25
forum: Desktop Environments
---

### Post by Treviño on 2006-07-25
Hello, I'm using a PC with an ATi card with fglrx drivers installed and I run an XGL server (with compiz, obiouvsly) in display :1.

My problem is running OpenGL based applications (like google earth :P or VMWare with DirectX support) in a Xnest session..
I know that I can run them in :0, but also using kwin/metacity (ran in :0 to manage windows) I can't have a good windows menagement...
So I knew that I colud use Xnest to open a new X session into my session and it does it, but... There's a problem, a big problem: in the new X session that I open I've no DRI support (and so no OpenGL :()...
Running fglrxinfo in DISPLAY=:2 I got two different errors:
```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
```(this one is recent, I got it only after editing gdm.conf file, it should disappear after resetting my gdm settings)

Or

```
 Xlib:  extension "XFree86-**DRI**" missing on display ":0.0".
display: :0.0  screen: 0
```
That's simply the same I get if I do fglrxinfo from XGL...

Suggestions?

I've tried also to run "gdmflexiserver -n", but I get an error regarding my .Xauthority file, but I don't know how to fix it.

Bye and thanks for attention ;) :KS

---

### Post by adam.tropics on 2006-07-29
shameless bump!

---

### Post by Anduu on 2006-07-29
You could probably pull this off if you were using and nVidia card...unfortunately us ATI users are out of luck.

---


---
title: "Fusion works on Gnome, but not on KDE"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by info54 on 2007-07-31
I'm using Ubuntu Fiesty (7.04). I've installed the restricted ati drivers, xorg and compiz fusion packages. I then installed the kde-desktop package and kubuntu-fi everything. Everything is OK. I created a shell script to start xorg for a gnome session. Everything works. I do compiz--replace and all the effects come up and everything is smooth and working. I change the script to start KDE instead and while KDE DOES start, it's really really sluggish (without compiz loaded). I load compiz and that work too, kinda. But again everything is very laggy and like there are shadows for the KDE menu, but it's got a white background underneath.

I don't get why it works for gnome and not KDE. I'm using the exact same script to start the session, just changing the last line from:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
dbus-launch --exit-with-session gnome-session
```

To:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec startkde
```

Is KDE different somehow and needs to have XGL loaded in a different way for it to work? It's like it doesn't switch direct acceleration on.

Any suggestions?

---


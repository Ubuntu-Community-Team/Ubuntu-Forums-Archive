---
title: "Ubuntu and VNC at login screen"
date: 2006-01-16
forum: Desktop Environments
---

### Post by diamondsw on 2006-01-16
Okay, I've had VNC up and running before. I've used various things in the past, from xf4vnc to x0rfb, etc, so I'm quite familiar with the hairiness of it all. On Ubuntu, things had always worked smoothly, but now for whatever reason  things are not working.

The last thing I had used was the instructions found at [RealVNC]("http://www.realvnc.com/products/free/4.1/x0.html"). Last I knew, this worked fine.

Tonight, I tried to VNC in, and found no VNC server was running. In my Xorg log was the following:

```
(II) LoadModule: "vnc"
(WW) Warning, couldn't open module vnc
(II) UnloadModule: "vnc"
(EE) Failed to load module "vnc" (module does not exist, 0)
```

So, obviously vnc.so wasn't loading for some reason. I double checked the vnc.so file and the vnc passwd file and finally my xorg.conf - everything was fine. All packages are up to date, using the various "vnc4" packages.

On the advice of another post here, I renamed the vnc.so file to libvnc.so, and now it loaded, according to the log:

```
(II) LoadModule: "vnc"
(II) Loading /usr/X11R6/lib/modules/extensions/libvnc.so
(II) Module vnc: vendor="RealVNC Ltd"
        compiled for 4.2.0, module version = 1.0.0
        Module class: XFree86 Server Extension
        ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension VNC
```

Unfortunately, this is one step forward, two steps back: now my machine freezes HARD when I connect. :mad: 

Before anyone suggests it, no, vino and "Preferences->Remote Desktop" is not an option, as those solutions are Gnome-based and cannot access the login screen if needed. One log out and I'm dead in the water.

---

### Post by diamondsw on 2006-01-16
Okay, who screwed the pooch on this one? The most I can glean from [this german page]("http://www.ubuntu-forum.de/post/31283/lastpost.html#post31283") is that Xorg for some reason is hard-coding loading "libvnc.so", but something else in the system is hard-coding "vnc.so", so the only way to make it work is to link one to the other. It *seems* to work - I can load the desktop and the login screen via VNC, but stability has gone way south - lots of listening to the disk churning itself to death and other issues, although I can't tell if that's due to VNC or the constant resets I had to do earlier due to its crashing. :(

Is there a bug entered for this one? If not, who owns it (Ubuntu? RealVNC? Xorg?) so I can submit one?

---


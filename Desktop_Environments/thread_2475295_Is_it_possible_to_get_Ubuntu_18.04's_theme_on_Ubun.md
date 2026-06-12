---
title: "Is it possible to get Ubuntu 18.04's theme on Ubuntu 22.04"
date: 2022-05-21
forum: Desktop Environments
---

### Post by thehangel on 2022-05-21
Hi, is there a way to install Ubuntu 22.04 and change the interface/GUI (windows header, icons, animations, etc...) to look like Ubuntu 18.04 ?
Thanks.

---

### Post by TheFu on 2022-05-21
Perhaps, but since 18.03 is Gnome3 and 22.04 is Gnome4.2, it isn't just a straight copy.  I'd assume everything involved would need to be translated from GTK+v3 to GTK+v4.

I suppose others may be interested, so let us know how your work goes.

OT, but related: A few years ago, I got tired of the GUI changes and stopped by going with a window manages, WM, only setup.  Each new Canonical release doesn't change my GUI at all. My workflows are optimized and since the WM I use hasn't changed too much since 2005, there hasn't been much undesired change.  OTOH, I had to customize it and do make a few changes manually each year.  In the beginning, I started with the defaults of the WM setup, which can suck. Fortunately, about 50 people in the same lab all used the same WM when I first started using v1 of the WM (1995), so I could see some amazing techniques for the use of workspaces.  Back then, I'd use a 3x3 workspace. Today and for the last decade I've been using a 3x1 workspace.  Monitors are bigger now and we have more of them. ;)  It is handy to have very different workspaces for specific types of work and NOT to have the clutter+bloat that most DEs bring.  Of course, this setup isn't for everyone.  

Find what you like and stick with it, but with greater complexity (GTK+ is very complex), there are many, many, more dependencies.  My fvwm2 setup doesn't have many dependencies at all. That's the good thing about extremely mature code.

---

### Post by Frogs Hair on 2022-05-21
The light-themes package(ambience&radiance) is still in the repository and the old icons may already be installed, but the gnome shell animations have changed a lot since 3.28 . ```
sudo apt install light-themes  
```

---


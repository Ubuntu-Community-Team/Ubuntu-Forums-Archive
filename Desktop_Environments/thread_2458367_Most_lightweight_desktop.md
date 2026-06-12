---
title: "Most lightweight desktop?"
date: 2021-02-22
forum: Desktop Environments
---

### Post by linuxartist on 2021-02-22
Is there a desktop environment which puts the least demands on hardware, while still allowing the running of 2D and 3D graphics software: Inkscape, Gimp, Scribus, Krita, Blender?

Thank you!

---

### Post by TheFu on 2021-02-23
I don't think a DE is related at all to which software can be run when those thinks aren't specifically tied to the DE ... like some of the Gnome3 panels.  I know Gimp works fine without any DE.  I use fvwm as my window manager, WM, without any DE. Bet all those programs will work 100% fine.

You can try openbox. I ran that for a few years back when LXDE used it as the default WM under the LXDE panels.

On Unix systems, the DE is just another program layer. Swapping them out is pretty easy.  It isn't the OS.  To completely change GUIs, takes about 3 minutes. A warning - some DEs are related and they use the same libraries and settings, but some of those settings have slightly different meanings under each DE.  That can lead to conflicts and not being able to login.  

The safest way to try different DEs is to create a few temporary userids and use each for a different DE.  You can have as many installed on the same system as you like. There are not conflicts that I'm aware.  All settings for each userid are stored in the User's HOME directory. When we create a new userid, almost always a new HOME directory is created at the same time. This is handy for all sorts of reasons.

---

### Post by guiverc on 2021-02-23
Your programs mean no desktop will be lightest for all.

**Krita**

Krita for example is a Qt5 based program that requires KF5 - [https://packages.ubuntu.com/hirsute/krita](https://packages.ubuntu.com/hirsute/krita)

so it'll be lightest with LXQt or KDE.  Usually LXQt is lighter than KDE, however Krita needs KF5 and Lubuntu/LXQt doesn't use KF5 so the lightness will be lost for that program I suspect.

**GIMP**

Gimp however is GTK(mostly 3 alas still parts 2) meaning it won't be as great with LXQt/KDE as the desktop will be using different libs (Qt5) to the application, so a GTK environment is better there - [https://packages.ubuntu.com/hirsute/gimp](https://packages.ubuntu.com/hirsute/gimp)

You haven't mentioned a release, so for Gimp the results will vary on release as well (Xubuntu wasn't fully GTK3 like Gimp is with 18.04, however was fully GTK3 for 20.04 & later)...  Gimp itself will vary on releases as well.


I've just talked about 2 of your listed programs, but just those two use different toolkits, libraries thus the DEsktop that each will run best in, won't be the best for the other.

You should thus maybe also consider
- How often will use each?
- How much RAM will you have? 
- What will be used at the same time (thus causes multiple libraries that do the same thing to share your RAM at the same time)
- etc..

You're asking for an answer to a contradictory set of conditions..

Also please note - these issues exist equally well for windows or other OSes.  The default for windows or MacOS is just for programs (Qt5 or other) to recommend a slightly higher memory requirement on their packaging, without any mention of the toolkit/libraries of the program in the box (*that's technical detail that tends to scare off buyers*).

---

### Post by TheFu on 2021-02-23
And let's not forget which packaging system is used can impact the amount of ram needed. By avoiding snaps and flatpaks, you can definitely reduce the amount of ram needed by the libraries at runtime.  Ask any C programmer to explain. In short, snap packages could force 2 (or more) copies of slightly different library versions to be loaded at runtime.  If the system has 32G of ram, it probably doesn't matter.

If multiple snaps use the same version of a library, then that code should be shared inside the snaps, but most snaps are out of synch.

---

### Post by ActionParsnip on 2021-02-24
The lightest desktop will be not a desktop environment but just use a tiling window manager on its own like Fluxbox, Openbox, FLWM or similar.

---

### Post by andrew.46 on 2021-03-01
Your best bet would be Fluxbox, all the applications you mention work well with this while Fluxbox itself treads quite lightly on resources. I have been running Fluxbox on this system for many years now, always a great experience Strictly speaking this system does not run Ubuntu as its base and I believe that Fluxbox on Ubuntu might be a little 'heavier' but still a good choice for you :)

---

### Post by similar2 on 2021-03-02
KDE Plasma (full DE) or Enlightenment (desktop shell) on Ubuntu. Both are highly optimized desktop environments and run beautifully - even on old hardware.
Or any desktop environment on Arch Linux ;)

---

### Post by ActionParsnip on 2021-03-02
[https://www.techradar.com/news/software/applications/5-of-the-best-lightweight-window-managers-for-linux-972570](https://www.techradar.com/news/software/applications/5-of-the-best-lightweight-window-managers-for-linux-972570)

---

### Post by othersamo on 2021-03-06
If you want to go as lightweight as possible, I would recommend using only a Window manager. It may be a bit cumbersome to get used to it, but once you do, you will be very effective using your system. The most common desktop managers are:
i3wm, awesomewm, bspwm (hopefully correctly pronounced).


If you, however, need to use a desktop environment, I would suggest XFCE or KDE Plasma 5.

---


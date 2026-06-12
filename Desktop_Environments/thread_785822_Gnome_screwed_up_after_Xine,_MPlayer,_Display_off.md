---
title: "Gnome screwed up after Xine, MPlayer, Display off"
date: 2008-05-07
forum: Desktop Environments
---

### Post by Jetze on 2008-05-07
Hi,

When I use Xine or MPlayer, or after the system had turned off my display in power save mode (so NOT when only the screensaver had been activate) Gnome is messed up: It looks fine for the first couple of seconds, but then the desktop goes black, although the top panel remains visible. Desktop comes back if I click one of the top panel menus (Application, Places, System). Sometimes only part of the desktop disappears, and sometime only part of it comes back. A few seconds after that, it gets worse: The entire screen seems to become wrapped horizontally by an offset of about 30 pixels or something, so the minimize, maximize and close-buttons appear at the far left of my screen. After that, the entire screen gets the grayish color of some of the gnome controls and clicking has become useless: no response.

Ctrl-Alt-Bksp at this point is mostly useless as well: just a black screen appears after a couple of resolution switches, whereas if I do Ctrl-Alt-Bksp when I can still see the top panel menus, I get the usual login screen. However, after logging on, the problems remain the same, eventually crashing Gnome. Same holds if I logout, but I suppose that's the same thing.

I tried to kill gdm from within another session after Gnome had crashed, but to no avail, although I do not know what is needed to restart X completely. After killing gdm, xinit would succeed, but I would still only see a black screen and hear the resolution switches in my monitor. Also, I do hear the short Ubuntu login prompt drum-like sound (login music is turned off) both after Ctrl-Alt-Bksp, and xinit.

I do not have this problem when using Totem. I suppose because it uses gstreamer, or are gstreamer and xine not distinct 'choices'? 

I think it migth have something to do with the fact that I am using an external monitor (1600x1200) connected to an Acer 5630-series laptop, which has a different native resolution, although I do not use the laptop screen: it's been turned off in Screen Resolution. I'm using Hardy Heron

So, what more information do you need to help me?

---


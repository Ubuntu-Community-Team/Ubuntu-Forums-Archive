---
title: "Gdm hangs, xorg goes to 100% CPU usage"
date: 2008-05-21
forum: Desktop Environments
---

### Post by mdeen on 2008-05-21
Hi,

I have some issues with my laptop and Ubuntu 8.04. Laptop is an Acer Travelmate 4001.
It started with the fact that I can not install any 8.04. 8.04 Server gave a message at first boot after installing that the image was of the wrong kind (or something similar), 8.04 desktop hangs at the first or the second screen in setup (the screens where you choose the localization or the timezone) and the alternate CD just won't boot.

So I've done the upgrade from 7.10 desktop to 8.04 and now gdm goes crazy.
Gdm just hangs, only the mouse moves but nothing can be clicked and no text can be entered. Xorg goes to 100% processor usage and the load went to 10 in a few minutes. All my ssh terminals locked up when I entered a command. Stopping GDM the nice way didn't work (terminal locked). Killing Xorg didn't work (terminal locked). Shutdown didn't work (yes, terminal locked). I had to physically turn the laptop off.
After rebooting, the same game, but I was able to kill gdm now and the system came to rest.

The only possible logmessages of interest are likely to be these from gdm/:0.log:

[FONT="Courier New"]mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
[/FONT]
Lots and lots of these lines, some 1000 of them.

What is going wrong here?

---

### Post by Doc on 2008-09-03
I'm having this issue currently on my desktop running Hardy. Seems to occur most often when switching users with GDM. Same errors in Xorg.log:

mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late

Based on a Google search this bug is not limited to a particular graphics card, driver or distribution. There is an entry on the freedesktop.org bugzilla:

[http://bugs.freedesktop.org/show_bug.cgi?id=14633](http://bugs.freedesktop.org/show_bug.cgi?id=14633)

Hopefully a fix will come soon.

hs

---


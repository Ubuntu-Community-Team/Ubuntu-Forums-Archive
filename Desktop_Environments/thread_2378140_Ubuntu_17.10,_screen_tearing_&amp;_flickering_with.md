---
title: "Ubuntu 17.10, screen tearing &amp; flickering with gnome session, but not with cinnamon"
date: 2017-11-20
forum: Desktop Environments
---

### Post by sennendog on 2017-11-20
I have a weird issue with 17.10 (upgraded from 17.04):

The system is configured with X11 with the proprietary nvidia driver and nvidia prime (intel skylake iGPU, nvidia 960M dGPU).
Prime synchronization is working for me, so there should be no tearing whatsoever, whether a window manager is compositing or not.

Using my usual Cinnamon desktop, all is fine. No tearing, flickering or so.

Starting a gnome session (either as ubuntu flavoured or stock gnome), I have *massive* tearing and flickering when dragging any sort of window.

Its the same X11 config and drivers as with Cinnamon, so I dont understand how this can be...
Anything I can configure for gnome to enable/disable compositing, vsync, redrawing...?
gnome-tweak-tool doesnt seem to be able to configure any of this...

Any hints or ideas??

---

### Post by mrprobot on 2018-02-02
This should fix it:

[https://community.linuxmint.com/tutorial/view/2304](https://community.linuxmint.com/tutorial/view/2304)

---


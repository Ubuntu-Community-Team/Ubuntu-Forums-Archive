---
title: "Forcing nVidia to vsync OpenGL"
date: 2015-03-03
forum: Desktop Environments
---

### Post by Sir_Sword on 2015-03-03
Using OpenBox window manager without a compositing manager.

Lubuntu 14.04.2 with nVidia proprietary 346.47.

It used to be in previous versions of Ubuntu I could force any and all OpenGL content to vsync by going into the nVidia control panel > OpenGL Settings > check Sync to VBlank.  Whether the game or program I was playing had built-in vsync or not, if I checked this box, all OpenGL content would be forced to vsync.  This no longer works.

Now, if a game has built-in support for vsync, the graphics will vsync properly.  Accelerated video (libvdpau) vsyncs properly.  However, if a game doesn't have built-in support for vsync, it will no longer vsync no matter how I have the option set in the nVidia control panel.

So, I used to be able to force vsync for all OpenGL content (without using a compositing manager), but now vsync only works for programs that specifically support it.

How can I get vsync working across the board again, without using a compositing manager?

---


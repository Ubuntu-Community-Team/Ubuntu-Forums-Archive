---
title: "mplayer drivers"
date: 2006-06-02
forum: Desktop Environments
---

### Post by oncemore on 2006-06-02
i've just finished installing dapper and all the software that i need but i have a problem with mplayer...

when i opened mplayer fohe 1st time, the colours were all wrong (it was using xv driver), so i changed the driver to x11 and the colors were good...BUT when i cick the full screen button, the video area stays the same but the rest of the screen is filled with black...
totem with gstreamer can go fullscreen with no problems...
the colors in xine-ui are wrong with the default driver...
this is weird ](*,)

---

### Post by wmcbrine on 2006-06-03
That is odd.

The x11 driver is non-accelerated, and you can only do software resizing with it (which you'd have to do explicitly on the command line, I think). You might try sdl, or even gl.

---


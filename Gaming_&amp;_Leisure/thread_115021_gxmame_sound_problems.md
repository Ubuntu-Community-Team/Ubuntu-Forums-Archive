---
title: "gxmame sound problems"
date: 2006-01-09
forum: Gaming &amp; Leisure
---

### Post by Plosky on 2006-01-09
Even with the excellent advice concerning esd and aumix related in previous posts, xmame still won<t play any sound.  any advice ?

---

### Post by leech on 2006-01-09
First off, I know this is a question that may make you feel dumb....but is sound working in anything else?  If so.. then let's go onto the next...

Next I would try just running 'xmame <location of rom> from the command line.  That way we can see if it is due to xmame or gxmame that you have no sound.

I haven't had problems with gxmame's sound for a very long time.  Joystick support in Dapper needs to be better, but that's for another day....

Leech

---

### Post by zneastman on 2006-05-23
Try changing the xmame binary.  If you're using xmame.x11, try xmame.SDL or one of the others (if there are others).

With xmame.SDL, you can choose which sound system (ALSA, OSS, or ESD) SDL (and consequently xmame) uses by installing the libsdl-alsa, libsdl-oss, or libsdl-esd libraries.  I couldn't get sound through xmame.x11 because it for some reason only allows ALSA or ESD as backends, neither of which are working well for me right now -- something about ALSA in Dapper is still borked (at least for me).  Installing xmame.SDL and libsdl-oss solved my problems because it forced xmame to use OSS as a backend.

If you want to check which sound systems are working (and which backend to use), try gstreamer-properties.

Nate

---


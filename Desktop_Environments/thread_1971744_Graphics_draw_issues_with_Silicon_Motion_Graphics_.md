---
title: "Graphics draw issues with Silicon Motion Graphics  in ThinkPad"
date: 2012-05-02
forum: Desktop Environments
---

### Post by ToniCipriani on 2012-05-02
Trying to revive an old machine here, installed 12.04 on an CF card and plugged it into my old ThinkPad 240Z using VMWare, since the machine doesn't have a CD-ROM (well, a bootable one at least, just an old honkin' PCMCIA one.)

All is well and things run pretty smooth, except for one thing: screen draw issues, see this:

[img]http://img214.imageshack.us/img214/4166/cimg0098u.jpg[/img]

Strangely, it goes away if I have Chromium or LXTerminal opened on maximize, and happens only on other applications that uses window manager cons of some sort (e.g. Pidgin, control panels, etc).

I checked the siliconmotion driver is already installed in Synaptic.

---

### Post by ToniCipriani on 2012-05-04
Bump... any ideas please? Thanks.

---

### Post by ToniCipriani on 2012-05-18
Found out what it was. Turns out it's not LXDE but the siliconmotion driver in Xorg. Turned off Graphics Acceleration and problem went away. Though I hope the Xorg guys will fix this some time because without harware acceleration it's kinda slow.

Added the option "NoAccel" in my xorg.conf and it was all good.

---


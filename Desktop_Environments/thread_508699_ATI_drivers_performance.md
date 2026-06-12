---
title: "ATI drivers performance"
date: 2007-07-24
forum: Desktop Environments
---

### Post by PhinnFort on 2007-07-24
I have an ATI Radeon 9800 XT, with an R350 chipset. I use the open source drivers (the ones that comes by default, "radeon" or "ati" in the xorg.conf file), and I used to have horrible performance. The rubberband (click-drag-select icons thingy) was horribly slow, and browsing certain websites, like Digg.com in konqueror was terrible, I could see the rendering of the screen, and scrolling wasn't very pleasant. Also the usually-fast Opera experience was terrible.
But, I found a solution.
In the Device part of your xorg.conf, add the following line:
```
        Option "XaaNoOffscreenPixmaps" "true"
```
(Somewhere between "Section "Device"" and "EndSection").
This disables the storage of offscreen pixmaps when using the XAA rendering technology. It isn't documented in the radeon manpage, but I found it on some obscure forum.
I know others have similar problems with the open source ati drivers (talked on IRC), so I thought I'd share the solution.
Oh, and my next computer is going to have an integrated Intel graphics chip;)

-PhinnFort

---

### Post by ft2482 on 2007-10-24
thanks for the tip

---


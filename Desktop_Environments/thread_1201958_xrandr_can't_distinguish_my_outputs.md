---
title: "xrandr can't distinguish my outputs"
date: 2009-07-01
forum: Desktop Environments
---

### Post by CornedBee on 2009-07-01
Hi,

I just switched from Gentoo to Kubuntu, and as a consequence I also switched from ATI's binary driver to the open-source driver. Now my dual-screen setup won't work anymore. I only get clone mode, which is simply useless.

I have a no-name X1550 (RV516) card which I'm inclined to blame for the problem, since it isn't the first time it's given me problems, but I'd much prefer a workaround to having to replace the card - it's an old board with an AGP slot, and whatever I'd get would be just as bad as what I have now.

Anyway, since KDE's display setting panel is useless, I try the xrandr console client directly. The information output looks pretty good:

```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2560 x 1024
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0     60.0*
   1152x864       75.0
   1024x768       75.0     70.1     60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        75.0     72.8     66.7     59.9
   720x400        70.1
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+
   1152x864       75.0
   1024x768       75.0     70.1     60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        75.0     72.8     66.7     59.9
   720x400        70.1

```
I had to manually add a Virtual line to the config to give it enough space, but the virtual screen should now be big enough to give me the two screens next to each other. However, if I then try to position them:

xrandr --output VGA-0 --right-of DVI-0

both screens go blank for a few moments and then come back up in clone-mode again. Doing it the other way round has the same effect.

Out of curiosity, I then tried this:

xrandr --output VGA-0 --rotate inverted

But this inverts *both* my screens, not just one. Same thing happens if I try to change the mode of one screen. It's as if xrandr cannot distinguish between the two outputs.

Any idea what could be causing this, and how to fix it?

Alternatively, is there any way at all to use the binary drivers? With R5xx support having been dropped before X.org 1.6 support was added, I don't think there is, but it's worth asking.

My xorg.conf is standard except for the Virtual line. My Xorg.0.log is attached.

---


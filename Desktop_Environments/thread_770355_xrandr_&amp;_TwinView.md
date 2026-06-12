---
title: "xrandr &amp; TwinView"
date: 2008-04-27
forum: Desktop Environments
---

### Post by mriedel on 2008-04-27
I use an nvidia TwinView setup. 2x 1680x1050 in TwinView mode (no dual X servers, no xinerama), so 3360x1050 from X's point of view. If a fullscreen application or me using xrandr changes the resolution to singe-display, say 1680x1050 or 640x480, thus turning off the second display, i can't properly turn it on again through xrandr. xrandr --output default --mode 3360x1050 does turn on the second monitor and it does set its resolution to 1680x1050, but I get a black bar at the top that seems to be the same size as my primary display's top gnome panel. The black bar is (corruptedly) paintable by application windows but doesn't redraw properly.

---

### Post by mriedel on 2008-04-28
bump

---

### Post by mriedel on 2008-05-01
bump

---


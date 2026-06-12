---
title: "KDE4.2 moves plasmoids after coming out of &quot;tv-out&quot; mode"
date: 2009-04-23
forum: Desktop Environments
---

### Post by utkjamie on 2009-04-23
Strange problem that started with KDE 4.2 under Intrepid and continues under Jaunty. I usually drop my plasmoids on the lower part of the desktop just above the task bar and usually this isn't a problem. However, whenever I switch to "TV-out" mode and then back to normal, KDE seems to retain the boundaries of the lower resolution in the upper-left section of the desktop. My plasmoids are moved to the upper-left section of my desktop and dragging them back to their previous positions causes them to snap back to this area of the desktop. It only happens if I unlock widgets and doesn't resolve until I restart the desktop.

I am using an ATI Radeon 9000 (RV 250) video card with the open source driver. Since there is no official support for tv-out, I use a bash script to switch in and out of TV-out mode. Here's what I'm using:

```
xrandr --addmode S-video 800x600
xrandr --output LVDS --mode 800x600 
xrandr --output S-video --mode 800x600
xvattr -a XV_CRTC -v 1
```

And the following to switch back to normal mode:

```
xvattr -a XV_CRTC -v 0
xrandr --output LVDS --mode 1400x1050
xrandr --auto
```

---

### Post by Zorael on 2009-04-23
Sounds like a genuine bug. To the [launchpadmobile](http://launchpad.net/ubuntu)!

---


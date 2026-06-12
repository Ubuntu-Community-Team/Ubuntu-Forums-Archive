---
title: "HOWTO: Dell Mini 9 + External HDTV"
date: 2009-04-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jbowden on 2009-04-08
I had a lot of trouble getting my Mini 9 to properly drive my 720p-1360x768 HDTV, at the right resolution, and keep compiz (DRI) active, and make sure that any videos didn't crash.  I found everything was fine if my HDTV was at 1024x768, but not at a 16:9 1360x768.

**The big issue:**  The intel 945GME in the Mini 9 can't map textures larger than 2048x2048.  So if you try to run your mini at 1024x600, and an HDTV at 1360x768, your combined size is 2384x768.  Totem, Mplayer, VLC all crashed with an X11 BadAlloc error.

**The fix:**  Don't place your external display to the right or left of your mini display.  Make sure it's above or below -- that means you're inside the max texture size.

In your xorg.conf, make sure you have:
```

Section "Screen"
...
SubSection "Display"
Virtual 1360 1368
EndSubSection
...
EndSection

```

I've had to use xrandr to adjust my screens still, since the GNOME display configuration doesn't seem to remember the position of an external display:

```

#HDTV
xrandr --output VGA --below LVDS --mode 1360x768

#OFF
xrandr --output VGA --off

```

---


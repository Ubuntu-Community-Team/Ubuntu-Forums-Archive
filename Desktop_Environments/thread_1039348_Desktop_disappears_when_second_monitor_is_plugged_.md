---
title: "Desktop disappears when second monitor is plugged in"
date: 2009-01-14
forum: Desktop Environments
---

### Post by noelsusman on 2009-01-14
Here's my problem,

Every time I plug my laptop (1280x800) into my second monitor (1680x1050), my desktop disappears.  Any files or icons that are supposed to be there are gone, but they still are there in nautilus.  When I try to change my background, nothing happens.  However, when I set my bar at the top of the screen (I don't know what it's called) to 50% opacity, I can a sliver of the new wallpaper behind that bar.  When I restart X, the new wallpaper is applied to the whole screen, but my desktop is still gone.

Everything works perfectly when I am not plugged into this monitor, and it even works fine when I plug my laptop into my TV via HDMI, so the problem seems to be in this specific monitor.  The only problem with that is that my roommate has the same model monitor and same model laptop that is also running ubuntu 8.10, and his works perfectly fine.

Basically, I'm lost and this problem makes no sense.

---

### Post by utnubuuser on 2009-01-14
Have you tried "sudo dpkg -reconfigure xserver-xorg", then "ctrl+alt+backspace"?

---

### Post by noelsusman on 2009-01-14
I just did it, but the problem still remains.

Here is my xorg.conf file if that is helpful.

---


---
title: "Terminal Server Client / VNC viewer scrollbars"
date: 2006-09-24
forum: Desktop Environments
---

### Post by atrophic on 2006-09-24
Whenever I use any sort of vnc viewer (tsc, tightvnc, etc) to connect to a vnc server, if the server's resolution is higher than that of my desktop I get scrollbars, which is great.  But they don't work, which isn't so great.  They show up as solid black scrollbars for the area I'm viewing, and white for area I can scroll to (no arrows for up or down, and the normal graphic for the area to click and drag is missing).  I can scroll down or right by clicking the white area, but I cannot scroll back up or left by clicking the white area on the opposite side, and since there are no arrows I'm stuck viewing the bottom or the right of the desktop.

Does anybody else have this problem?  I have it on three separate computers.  Is there a way to fix this?  Another viewer that doesn't have the problem perhaps?

---

### Post by ebel_ on 2006-10-05
Yeah I have the same problem, not sure how to fix it yet.

---

### Post by ronniew on 2006-10-07
I have discovered that if you want to scroll left right up down click using the mouse scroll wheel

---

### Post by atrophic on 2006-10-07
> **ronniew said:**
> I have discovered that if you want to scroll left right up down click using the mouse scroll wheel

That's good to know, but my mouse's scroll wheel is broken, and the behavior is still not what it's supposed to be.  The viewers work fine on my windows machine at work, but none of the 3 ubuntu servers there or 2 I have at home have vnc viewers with scrollbars that work properly.  I find it hard to believe this problem isn't wider spread.

---

### Post by neocon2005 on 2006-10-11
The scrollbars are age old X design. They don't behave like modern scrollbars. For example to scroll down, left click on the right side scrollbar and right click scrolls up. Similarly to pan right (left click) and pan left (right click) on bottom scrollbar.

I think the terminal server program in Gnome is by far the worst app. Fullscreen mode does not work (for VNC atleast). The KDE 'version', krdc is lightyears ahead. Gnome devs... please please please fix it.

---

### Post by atrophic on 2006-10-12
Thanks for the information neocon2005, I'll give those a try and VNC might finally be usable for me.

---

### Post by bb002 on 2006-11-06
vnc4 is in the repositories. Think it is universe.

just install the xvnc4viewer and vnc4-common. then remove xvncviewer and and vnc-common.

This will update you to VNC4 instead of the old 3.3 version that comes instaled by default. Scroll bars also work like expect in VNC4.

---

### Post by &#12465;&#12452;&#12488; on 2006-11-06
Oh, thanks so much for the tip, bb002!! Version 4 was so much better to use, mmm.

---

### Post by voam on 2007-03-16
bb002,

You just made my life a little bit easier.

Thanks

---


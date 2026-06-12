---
title: "How to disable the screen being larger than the physical screen?"
date: 2009-06-07
forum: Desktop Environments
---

### Post by Buntuuser01 on 2009-06-07
Hello y'all,

I've recently installed Ubuntu 9 Jaunty to use it as a mediacenter w/ XBMC. I need to be able to set the screen resolution to 800x600 to properly display xbmc on my television. However, when I set 800x600 to be the first mode in the *"Screen"* section of my /etc/X11xorg.conf the resolution that my computer uses is, indeed, 800x600. However, if I move my mouse to the left or to the right the screen scrolls to the L or the the R too. That is, the "real" resolution that Xorg uses to display the desktop is the second mode from xorg.conf: 1280x960, be it cropped to 800x600. I use that mode when I use my PC on a regular monitor, like now when I'm typing this post. ;)

How can I modify my xorg.config in such a way that the real resolution is does NOT stretch beyond the physical boundaries of my monitor? I clearly remember the *xfree86conf *program to ask you that in the past. But Xorg does no longer have a config utility. So one must find that out oneself now a days...

---

### Post by zhocchao on 2009-06-07
maybe

xrandr -s 800x600

helps?

---

### Post by Buntuuser01 on 2009-06-07
Yes it does. But I'd like start up Ubuntu with the proper resolution without running xrandr -s 800x600 and 1280x980... There must be a way...

---


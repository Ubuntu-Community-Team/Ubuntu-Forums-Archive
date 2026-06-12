---
title: "xorg.conf Input Devices"
date: 2007-10-19
forum: Desktop Environments
---

### Post by caecus314 on 2007-10-19
This isn't a major problem or anything, but I'm hoping some of the experienced Linuxers that roam these forums can help me out.

I do not understand the syntax of the xorg.conf file.  I have been searching the Internet for some time, and I cannot seem to find a definitive manual for the file anywhere.  Is there some obvious site that I have been overlooking?  It baffles me that a file that offers so much control over the Linux desktop environment has so little documentation.

If I'd been able to find documentation for the file, I might have been able to figure out how to do this on my own:

I recently bought a brand new Lenovo T61p, which happens to come with both a nub and a touchpad for mouse navigation.  For some reason, I have always greatly preferred the nub, so I generally use it and simply ignore the touchpad; no problem.  But... seeing as the touchpad is still there, I thought it would be cool to put it to use somehow.  I would like the nub to move the mouse cursor around the screen, and I would like the touchpad to scroll both vertically and horizontally within windows.  After playing around with xorg.conf, I was able to get this effect to work, but only for the bottom and right edges of the touchpad.  I would like to devote the entire touchpad to scrolling, and I would not like the touchpad to affect the position of the cursor at all.

If anyone has any ideas, please let me know!  I appreciate it.

---

### Post by rsambuca on 2007-10-19
[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

---

### Post by caecus314 on 2007-11-10
Well... thanks for the response.  That was actually one of the first pages I looked at, and although it does appear to be a manual of sorts, it is far from complete.  I'm looking for something that would explain exactly what all the Sections and Options mean.  Most of the keywords that come included in the default Ubuntu xorg.conf aren't even listed on that page.  They've got to be *somewhere* on the Internet, right?

...Or maybe I just don't know how to navigate the x.org manual?

I'm really sorry to whine so much.  Thanks for the help anyway!

---

### Post by rsambuca on 2007-11-10
I agree with you on this one.  It's like you have to hunt down and go through 20 different websites to find the one little piece of info on the xorg that you need.  I just pointed that one out to you because it was one of the better ones I have come across.  

There is also some really good info in the gentoo wiki as well.

---

### Post by caecus314 on 2007-11-10
Thanks.  I'll have to check there.

---


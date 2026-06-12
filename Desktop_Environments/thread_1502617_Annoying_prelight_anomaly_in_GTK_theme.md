---
title: "Annoying prelight anomaly in GTK theme"
date: 2010-06-05
forum: Desktop Environments
---

### Post by fredbird67 on 2010-06-05
I've got a theme I'm creating that's based on the US flag and is a port of a similar theme I found on E17-Stuff.  It's almost done, but there's one slight problem:  When I hover over a radio button or checkbox, I get white text on a #d5d5d5 background, which makes for very poor contrast indeed.

I tried grabbing a screenshot of this, opened it in the GIMP, and found that that color is #d5d5d5.  Well, I did the "find" operation on the theme, and lo and behold, that color isn't there (scratches his head).  What do I need to look for in the GTK theme that would fix this?

Thanx in advance,
Fred in St. Louis

---

### Post by fredbird67 on 2010-06-05
Never mind, I figured it out on my own.  It turns out it wasn't something in the GTK file at all.  Out of curiosity, I tried the "checkbox" folder, and found a file there that was a simple light gray square.  I opened it in the GIMP, took the color picker to it...and sure enough, its color was #d5d5d5.  So I changed it to something that contrasts much better. :-)

---


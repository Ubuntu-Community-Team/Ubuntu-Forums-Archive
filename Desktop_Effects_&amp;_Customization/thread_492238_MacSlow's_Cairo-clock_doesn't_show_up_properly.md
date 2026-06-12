---
title: "MacSlow's Cairo-clock doesn't show up properly"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by BrokeBody on 2007-07-04
Instead of clock, there's only a white box

[http://img110.imageshack.us/img110/6918/screenshotrm1.png](http://img110.imageshack.us/img110/6918/screenshotrm1.png)

Anyone knows how to fix this?

---

### Post by detroit/zero on 2007-07-07
I just installed Cairo Clock from Synaptic and I have the same problem.

---

### Post by detroit/zero on 2007-07-07
I got to tinkering with the settings and found that when I use the default sizes (small, med, large) the clock is a white square. If size is set to "custom" and you adjust either height or width by even one pixel the clock face appears.

Odd, but it works.

---

### Post by BrokeBody on 2007-07-07
Here's another problem now

[http://ubuntuforums.org/showthread.php?t=492552](http://ubuntuforums.org/showthread.php?t=492552)

---

### Post by detroit/zero on 2007-07-07
From Cairo Clock's description in Synaptic:
> 
It&#8217;s an analog clock displaying the system-time. It leverages the new visual
features offered by Xorg 7.0 [B]in combination with a compositing-manager (e.g.
like xcompmgr or compiz)[/B], gtk+ 2.8.6, cairo 1.0.2, libglade 2.5.1 and librsvg
2.13.93 to produce a time display with pretty-pixels.I don't exactly understand all the reasons behind it, but AWN for example behaves much the same way when Compiz is turned off - there's a big black line that surrounds the dock. Being as cairo-clock and awn both call for a composter as a pre-req for installation, I don't think this one's going to be a problem you're going to work around.

---

### Post by BrokeBody on 2007-07-07
And I suspected that it might be because of that. Well, there's a documentation which no one is reading. :p

---

### Post by ulisesrangel on 2007-11-24
yeah, i got the same white square

i read here that while not use standard size (small,medium,large) neither custom (128x128) it will show

that work for me, the clock show up with any custom size but 128x128

---

### Post by Forlong on 2007-11-24
You can use Screenlets instead (it's code is based on Cairo clock), it brings the clock (among others) with it as well as other goodies. :)

---


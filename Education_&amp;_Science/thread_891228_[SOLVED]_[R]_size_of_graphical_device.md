---
title: "[SOLVED] [R] size of graphical device"
date: 2008-08-15
forum: Education &amp; Science
---

### Post by Tart on 2008-08-15
Dear all,

I'm running R on my laptop. It has screen resolution of 1280x800. Whenever I create a plot in R (for example >plot(sin)), the default window have hight 800, so my bottom panel is in the way, it obstructs lower margins. See attached screen shot. It is not really big issue, but I sometimes put text on lower margins (subtitles). I'm little bit tired of manual resizing. 
I can control size of output all other devices (jpeg, pdf, ps, and so on). But how can I control default on the screen window?  I would like to resize it to maybe 750x750 or so, is there any file where can I specify parameter for default graph window size? 

Thanks

---

### Post by Tart on 2008-08-15
I solved this problem. For all those who have similar problem.

```

sudo gedit /etc/X11/Xresources/x11-common

```
add

```

R_x11*geometry: 700x700-0+0

```
to the end of file
700x700 - size of default graphical device. 0+0 puts in in top-right corner.

---


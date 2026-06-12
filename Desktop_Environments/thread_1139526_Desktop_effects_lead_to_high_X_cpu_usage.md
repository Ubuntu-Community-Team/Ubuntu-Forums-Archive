---
title: "Desktop effects lead to high X cpu usage"
date: 2009-04-27
forum: Desktop Environments
---

### Post by kprateek88 on 2009-04-27
I had been using Kubuntu 8.04 with KDE 3.5 and Compiz for a long time. Compiz worked fine.

I recently installed Kubuntu 9.04 with KDE 4.2 and decided to try KWin's compositing. However enabling compositing makes the system extremely slow. top shows very high CPU usage by X. This is in OpenGL mode. Trying to go to XRender mode causes a lot of screen-redrawing etc and comes back to OpenGL mode.

This is an Acer Aspire 4720 with an "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller".

Are there any other details I should provide?

---

### Post by inobe on 2009-04-27
there are problems with intel video.

i pointed a few to this

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

each of them claimed success.

---

### Post by kprateek88 on 2009-04-27
Thanks! I'll look into this. I'm a bit uncomfortable with the idea of installing an unsupported rc kernel, though.

---

### Post by inobe on 2009-04-27
at least when you do' the next time around you'd feel more comfortable.

---


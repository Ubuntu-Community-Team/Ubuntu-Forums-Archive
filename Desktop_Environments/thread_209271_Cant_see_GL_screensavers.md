---
title: "Cant see GL screensavers?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by floyd27 on 2006-07-04
Hey guys.. Iv messed with this for too many hours, so I must ask for some help.

I cant for the life of me get any GL screensavers to show.. Not even a preview. Is there a dependancy or patch I need to get these things going.?
I have a BFG 6800 with the nvidia drivers form automatix..

Thanx for any info...

---

### Post by soce_32 on 2006-07-04
Try this command: $ glxinfo | grep render

And you should get something like this:

direct rendering: Yes
OpenGL renderer string: GeForce FX 5200/AGP/SSE2

If you don't see this, check your /etc/X11/xorg.conf and make sure that the dri and glx modules are loaded and that you are using the nvidia driver.

---

### Post by floyd27 on 2006-07-05
Thanx for the info..
I ended up searching in synaptic for "gl" and "screensaver" I added everything that looked interesting and it worked. Im not sure what did it but its working now.
I was definatly a screensaver issue and not my vid card though..

---


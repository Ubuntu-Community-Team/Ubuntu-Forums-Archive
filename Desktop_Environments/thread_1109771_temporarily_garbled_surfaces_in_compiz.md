---
title: "temporarily garbled surfaces in compiz"
date: 2009-03-29
forum: Desktop Environments
---

### Post by rasmus_ on 2009-03-29
Hi,

I've been using compiz quite some time now and love it. I have but one small issue, and I'm under the conception that everybody "suffers" from this.

Sometimes when I start a slow-starting application, e.g. Open Office Writer and to some extent even firefox (even though starting firefox is quick) there is a moment when the surface representing the window contains random garbage that looks like stuff left in videomemory when the surface was allocated. This can quite frankly make the initial animation ugly.

Is there any way to make compiz clear a new surface or wait until the window has drawn itself before starting the initial animation?

This happens both on a laptop with Hardy and integrated Intel graphics as well as on a desktop computer with Intrepid and Geforce GTX 280.

---

### Post by Kevbert on 2009-03-29
The most likely cause of this is lack of memory as compiz is a hog. If you can add some more RAM it may help.

---

### Post by rasmus_ on 2009-03-29
Hmm.. My desktop system has 2 GB RAM and as of now the System Monitor reports a usage of around 400 MB. Also I have 1 GB video memory. Any other ideas?

Note that it only happens when a program is first started; the buffers aren't lost when the program is running. Also it doesn't happen with lightweight programs such as gnome-terminal so I guess the issue is that compiz doesn't clear the surface and the program has yet to draw itself when the initial animation is running.

If it matters I'm running a Intel Core 2 Quad at 2.4 GHz, but since I'm experiencing the same issue with my laptop (Intel Atom, 1 GB RAM and integrated graphics) it shouldn't be limited to my setup. Is there no one else experiencing this?

---

### Post by rasmus_ on 2009-03-31
Update: After installing the nvidia-glx-180 package on Intrepid the issue seems to be gone on my desktop computer :D

---


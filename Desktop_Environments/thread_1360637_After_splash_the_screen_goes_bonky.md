---
title: "After splash the screen goes bonky"
date: 2009-12-21
forum: Desktop Environments
---

### Post by Neuster on 2009-12-21
So after ubuntu goes past the splash screen and the resolution changes the screen overlaps.  I have probably 4 cursors, and there are horizontal lines, it's weird.  XP works fine, so I'm assuming it's a xorg.conf issue or something along those lines.  Or a resolution problem.

So how do I fix this?

---

### Post by Neuster on 2009-12-23
C'mon, this is seriously annoying.  I've been having to use Xp.  


So a better description.  After the splash screen it appears like the resolution is messed up, but i can't fix it.  

There are horizontal lines, but they dont go all the way across.  I have what appears to be 5 desktops, and they overlap.  I have several mice, but only one works, so it's pretty confusing.  **** this is hard to describe.

---

### Post by cprofitt on 2009-12-23
Please hit cntl+F1.

Login.

Then do the following command:

lspci | grep VGA

That should tell us what video card you have and allow us to help.

---


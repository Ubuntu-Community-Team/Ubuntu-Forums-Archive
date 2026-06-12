---
title: "missing icons"
date: 2012-08-28
forum: Desktop Environments
---

### Post by echeddar on 2012-08-28
I had an installation of OpenSuse on my laptop with the /home dir in its own partition.  I switched recently to Ubuntu, but it seems a bit iffy.  At first, it said programs were having trouble [writing, I think] to my home dir.  Rebooting seems to have fixed that.  But several icons are still missing from both the launcher and the dash.  Terminal, gedit, Filesystem icons, system settings, trash.  Basic stuff.  On the launcher I see a black square with a lightened gradient in the middle of the top.  On the dash, I see simple outlines of squares with diagonal hash marks patterning them.  I've looked around a bit, but can't find a recommendation that seems to fit this problem.  Thanks in advance for any ideas.

---

### Post by bogan on 2012-08-29
Hi!, **echeddar**,

I had a similar problem to that you describe, with some launcher Icons showing & others not; placing the cursor over a missing one, showed its name, but nothing worked when clicked.

That may not be exactly your problem, but I cured mine with:```
 sudo apt-get install --reinstall ubuntu-desktop
```Worth trying?

Chao!, **bogan**.

---

### Post by echeddar on 2012-08-29
Yes, that fixed it!  Thanks!

---


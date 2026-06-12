---
title: "Problems with Cube Rotate in Compiz Fusion"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by BuddMan on 2007-10-02
In Compiz Fusion, I only need a 2-sided desktop instead of the 4-sided cube that most people use.  I find no problems when I have to rotate a 4-sided cube, but when switching to a 2-sided "flat" desktop, when flipping sides, I get a flashing/garbled desktop until the rotation is complete.  Has anyone else experienced this and know a fix for it?

---

### Post by Dark Hornet on 2007-10-02
I am able to "flip" the desktop with no issues...can you tell me a little more about your set up...are you running Fiesty, what gfx card do you have, etc.

---

### Post by BuddMan on 2007-10-03
I'm running Feisty, have an Intel GMA 950 (it's a Dell e1705 laptop), and am running the latest Compiz.  The corruption only occurs on the desktop (if the desktop was to zoom out, you only see the corruption/flashing on it, not the entire screen).  I've tried disabling almost all plugins to see if any were the cause and still am having the issue.  It doesn't happen all the time though - usually I can flip the desktop with the mouse and don't see it, but if I try to drag a window to the other side, I always see it.  This never happens if I have the desktop with more than two sides (like a cube) - it only happens when the desktop is set to 2 sides.  Any  help would be appreciated as I'm at a loss as to what this could be.

---

### Post by BuddMan on 2007-10-03
Problem solved.  I switched to git packages and it no longer happens.

---

### Post by flarkit on 2007-10-13
Hi

I hope this is the right place to ask... I followed [Forlong's](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) guide for adding installing Compiz Fusion.

It works quite well. I'd just like to know how to disable the automatic 'switch event' when the mouse cursor approaches the horizontal edges of the desktop
:confused:

---

### Post by Forlong on 2007-10-13
> **flarkit said:**
> I'd just like to know how to disable the automatic 'switch event' when the mouse cursor approaches the horizontal edges of the desktop
That shouldn't be a default setting.
Make sure Edge Flip Pointer in the Rotate Cube plugin is disabled.

---

### Post by flarkit on 2007-10-13
> **Forlong said:**
> That shouldn't be a default setting.
Make sure Edge Flip Pointer in the Rotate Cube plugin is disabled.

That sorted it out perfectly, thank you yet again. I didn't enable it, so perhaps it is/was turned on by default, in fact

---


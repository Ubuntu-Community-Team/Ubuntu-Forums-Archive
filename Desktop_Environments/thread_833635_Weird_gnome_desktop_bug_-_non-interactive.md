---
title: "Weird gnome desktop bug - non-interactive"
date: 2008-06-18
forum: Desktop Environments
---

### Post by mike_b on 2008-06-18
I just re-installed Ubuntu 8.04 on my Dell M60 laptop.  It installed fine but I'm having a strange problem with the default desktop.  I seems to stop refreshing and icons are not clickable.  Left clicking works, but not on icons.  Strange.  Plus, trying to use the mouse to select multiple icons, leaves the highlighting boxes stuck on the background. 

I am using the nvidia restricted driver, and desktop effects disabled.  I switched drivers because color depth with the OSS driver was only doing 16bit, and gradients on the default background looked horrible.

Also moving windows seems to randomly maximize and restore them.

Here is a screenshot of what I  mean about the highlight boxes.
[ATTACH]74551[/ATTACH]

---

### Post by mike_b on 2008-06-18
As a follow up.  I tested and duplicated the same problems in the live CD using the OSS nvidia driver with its 16bit color depth horribleness.

---

### Post by mike_b on 2008-06-20
I was able to identify it has an issue with the touchpad that is causing the problem.  specifically the problem is when using the finger mouse on the keyboard, and the mouse buttons on the touchpad.  Disabling the touchpad solves the problem, but then I can't use the touchpad mouse buttons.

Is there a known compatibility issue with dell D800/M60 laptops?  This wasn't an issue in feisty or after upgrading from feisty to hardy.  Just a new install of Hardy brought this out.

---

### Post by mike_b on 2008-06-20
I solved the problem.  Changing the touchpad protocol from "auto-dev" to "event" in the xorg.conf solved all problems.

---


---
title: "Kiba dock icon problem"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by Fleece Flamingo on 2008-01-04
Whenever I enable physics the icons slip behind the dock. How can I prevent this?
[http://img223.imageshack.us/img223/9075/screenshotwx9.png](http://imageshack.us)

---

### Post by Fleece Flamingo on 2008-01-04
Bump

---

### Post by tyrantt23 on 2008-01-29
Well, this is my first post in any Linux-related forums, so I guess I'll <# Include> a brief introduction of myself. I first tried installing Linux a couple of years ago (Debian), but I couldn't get it to even start. I gave another go with Fedora about a year ago, and I loved all the eye candy. I decided to try Ubuntu last week, and I'm amazed by how much more user friendly it is to get all the settings working - as opposed to having to go to dozens of obscure files and settings to change random values that make no sense.

Anyway, I would say I know as much about UNIX/Linux as the average/advanced user knows. I love learning more though, so if you know of something that might be useful/interesting to learn, hit me up with a link! :P

**The Problem:**
Hey, I'm having the same problem as the original poster. When I activate physics, the dock gets placed on the foreground, partially covering the icons. I can't click or drag the icons that are behind the dock, only the ones that moved beyond the dock. I doesn't matter if it's set to rope, wobbly, spring, or dock. I also tried changing multiple values and settings in kiba-dock and Compiz to no avail. 

I've been googling for an hour but can't find the answer. I would think it's an easy fix, maybe changing a value somewhere. Post any link that might help... Thanks a lot! :P

[IMG]http://img150.imageshack.us/img150/7008/screenshotvl7.png[/IMG]

**Specs:**
AMD64 3200+
4GB RAM - Corsair XMS
BFG Nvidia GeForce 7950 (256MB)

---

### Post by tyrantt23 on 2008-01-30
a small bump to go please. :)

---

### Post by tyrantt23 on 2008-01-31
**UPDATE:**

I still don't know what was wrong that made the dock appear like in the picture above. The problem has been fixed after a fresh re-install of Ubuntu.

1. Right after the fresh install, I activated the Restricted Driver Managet under System >> Administration to retrieve my video card drivers (GeForce 7950).
2. Restarted computer. The video card was working properly now and I could activate Compiz Fusion.
3. I installed Kiba-Dock using [this shell script]("http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=540.msg2613#msg2613"). 

Installation went smooth, and the physics was working properly:
The dock was no longer in the foreground by default like on my previous post. When the physics was activated, the icons would bounce off and move around and they would remain on the foreground.
[[IMG]http://img172.imageshack.us/img172/3163/83748217mn9.png[/IMG]](http://imageshack.us)

However, whenever I clicked on the dock, all the icons would go to the background, and to bring them back to the foreground I'd have to click on them one at a time. I don't know if this is how it's supposed to work, but I consider it to be normal behavior, like how it works with windows going into background/foreground as you click on them.
[[IMG]http://img352.imageshack.us/img352/3868/87601383wj8.png[/IMG]](http://imageshack.us)

After that I started installing/configuring other applications - Compiz Config Settings Manager and all its dependencies, [3D Windows for compiz]("http://forum.compiz-fusion.org/showthread.php?t=5303"), and thunderbird. I tested kiba-dock after each install/configuration and its still working perfectly. :D

---


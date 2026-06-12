---
title: "Strange Xorg behaviour with multiple users"
date: 2007-11-23
forum: Desktop Effects &amp; Customization
---

### Post by koma77 on 2007-11-23
I'm confused.

I would be very happy if someone could explain what's happening...

I'm running the fglrx driver and it works OK.

When I log in as my standard user I cannot turn on desktop effect since the compositin extension is not available. That's alright by me. Also, DISPLAY is set to :0.0 which is fine. glxgears runs at about 8000 FPS.

The other day I created two new users on my system.

When I log in using those users, I noticed that DISPLAY was set to :1.0. And glxgears ran at 10000 FPS, i.e. 2000 FPS faster than for my normal user. Also, for some strange reason, desktop effects worked fine...

It's as if there is another xorg using a completely different setup?

And also: if I use the radeon (ati) driver, i get about 4000 fps in glxgears, so that's not what is happening.



My questions:

How come some users use :1.0 by default and others :0.0?

How can desktop effects work for some users but not others? It's the same xorg.conf in action, right?

---


---
title: "maximized windows are not really &quot;maximized&quot; in beryl"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by Gan Quan on 2007-08-11
Hi, I got a problem in beryl
the Maximize button on the title bar seems not work properly, every 'maximized' windows leaves a blank area on the right side of the screen. I got a wide screen LCD with 1280x800 resolution, it seems that beryl doesn't detect my screen width correctly.
I attached a screenshot, any input?
Thanks!

---

### Post by vhex on 2007-10-11
I was having the same problem with Gutsy (latest, but had that since day 1) on an Intel Mac Mini with Intel GMA950 graphics processor.  Xorg driver: intel, resolution: 1280x1024.  There would be a margin of about 200 pixels between the bottom of a maximized window and the bottom of the screen, although gnome panels were positioned correctly.  Without compiz everything worked fine.  This is how things have been since I installed the system, without manually touching any configuration.

I have just switched screen resolution to 1024x768 and back, now everything works fine.

By default, Gutsy used the i810 driver, which didn't support resolutions higher than 1024x768.  I had to install the xorg-video-intel driver with Synaptic, following a post on this forum, which fixed the problem.

Just for your information.  I don't know how to explain this.

---

### Post by Forlong on 2007-10-11
Gan Quan, what is that application in the bottom right corner of the desktop?

---


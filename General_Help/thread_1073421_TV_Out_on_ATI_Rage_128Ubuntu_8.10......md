---
title: "TV Out on ATI Rage 128/Ubuntu 8.10.....?"
date: 2009-02-18
forum: General Help
---

### Post by HeartBreak on 2009-02-18
Hi. I recently built a home media center/server (using older hardware), and I must say, I'm impressed. Everything worked right out of the box, even the media buttons on my keyboard (a Lite-On SK-7100 infrared keyboard with built-in stick-mouse).

 However, I am having one major hurdle that I've spent the last 2 weeks trying to tackle (with the aid of Google and this very forum).

 I simply cannot get TV out to work (either Composite or S-Video) beyond the X Server startup. I can see the bios post and the splash screen, but once it loads the X Server; bang! Black screen, and nothing to be seen.

 Pressing the power button sends it into shutdown mode, which causes the shutdown splash to display.

 Things I have tried;

 ATI's proprietary driver (fglrx); caused X Server to refuse to load.
 Vesa driver; seems like it didn't do anything different
 specifying "ati" and "r128" for device drivers in /etc/X11/xorg.conf; no change.

 I've tried setting the resolution down as low as can be, and still no difference. I'm at the point that I'm thinking a different video card might be in order, but I don't want to spend very much on a video card (as this server is an 800mhz dino-server).

 As such, is there a list of video cards that Ubuntu is known to display TV out on that are AGP 1x/2x?

 Thank you for your help in advance!

---

### Post by diskmaster23 on 2009-12-21
Did you ever find a solution?

---


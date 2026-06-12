---
title: "Panels revert to wrong monitor"
date: 2009-01-12
forum: Desktop Environments
---

### Post by cybergrunt on 2009-01-12
Hi, I'm running stock standard 8.10 on a Dell D620 laptop and I've managed to extend the desktop to a 21" IBM flatscreen. However when I reboot the computer the panels are on the IBM monitor instead of my laptop. I drag them across and that's fine, even if I log out and back in but if I reboot they come back up on the IBM monitor. It's not a life or death issue but it is kind of lame so I was hoping someone out there had a solution for me. I have found similar issues but nothing which really pertains to my problem.
Cheers in advance!

---

### Post by Neil Woolford on 2009-02-27
I'm also suffering from this problem when using an external projector to run OpenOffice presentations.

The panels appear by default on the projected image, not the laptop screen.

So far my workaround is to connect before the audience are around, then drag the panels (and any file icons) across to the laptop screen, to give a clean desktop on the projector.

I also have to set the slideshow preferences in OpenOffice to make sure that the presentation runs on the projector and the presenter console on the laptop, which again should likely be the default behaviour but isn't.

I suspect the answer may be buried deep in gconf, but haven't found it yet.

Neil

---

### Post by Neil Woolford on 2009-02-27
Not too encouraging so far.  I'm using Ubuntu 8.10 which uses Xorg RandR 1.2
to manage the displays and screens.

According to the wiki at [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) Gnome always puts the panels on the external monitor (at least with the hardware I'm using).

"Gnome places the menu bar on screen 0 and thus with the Intel chip and driver Screen 0 (the external VGA monitor) will always be the default display if it is connected."

Neil

---


---
title: "Ubuntu desktop manager broken - gnome restarts after login"
date: 2007-09-04
forum: Desktop Environments
---

### Post by krymson on 2007-09-04
Gnome doesn't want to load anymore.

I updated Breezy to Dapper, had some issues(locales mostly), fixed them, everything seemed absolutely dandy, so i upgraded to Edgy.

Things seemed ok, until i restarted. Now it lets me login once, but as soon as the loading screen finishes and the desktop starts to pop up, the desktop manager restarts itself and im back to the login screen. If i try to login this time, I hear the drums(startup sound), and then a blank screen and my mouse cursor, immovable. 

Things seem seriously wrong. I can boot up into recovery mode(command line), but the gui seems futzed.

Any Ideas or starting points? I'm pretty stumped.

---

### Post by banewman on 2007-09-05
I wonder if the update changed the video driver on you. From the command line type - sudo dpkg-reconfigure xserver-xorg - this will let you change settings for x. I would recommend only changing the video driver to - vesa - which is a failsafe. Select all the rest as defaults, and that should get you back in with any luck. :)

---

### Post by dingansich on 2008-01-22
This thread has been quiet for a while, but I figured I'd throw my experience in here.

I encountered the same problem experienced by the OP. I have no idea what caused the problem (my Gutsy distro was working perfectly).  Anyhow, after poking at the Gnome config and session files a bit - which did nothing - I just reinstalled my video driver, and voila!  I think compiz was encountering some kind of problem with the GL configuration.

First I tried using Envy, and that fixed the Gnome loading problem but did a poor job of configuring the desktop.  So I did a manual install of the nvidia driver and that did the trick!  

It seems like this problem pops up all over the place, and may be related to a number of potential issues, but in my case I just needed to reinstall the video driver.  So I can't guarantee that this will work in all cases, but hey, it's something.

---


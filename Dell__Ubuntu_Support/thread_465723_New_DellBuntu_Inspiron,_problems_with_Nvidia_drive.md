---
title: "New DellBuntu Inspiron, problems with Nvidia drivers"
date: 2007-06-06
forum: Dell  Ubuntu Support
---

### Post by thetictacaddict on 2007-06-06
I got my E1505N from Dell today and I'm excited and mostly everything is working great, but I'm having a serious problem.  I enabled the closed NVidia driver and was using it with no apparent problems, but when I tried to play a video, I hit trouble.  First I opened it with Totem, which froze up and closed.  Then I tried VLC, and everything locked up.  The mouse moved slow and jerky for a few moments, but eventually stopped all together.  The keyboard didn't seem to respond and I couldn't switch to a terminal with Ctrl+Alt+F1.  I held the power button until the laptop shut down.  When I turned it on, I heard the ready sound that GDM makes, but the screen was black.  I switched to a terminal, changed to the nv driver in xorg.conf, and everything seems to work now, including the video.  But I want the features of the nvidia driver!  If I switch back to nvidia I get a black screen.  What gives?

---

### Post by dmb on 2007-06-06
> **thetictacaddict said:**
> I got my E1505N from Dell today and I'm excited and mostly everything is working great, but I'm having a serious problem.  I enabled the closed NVidia driver and was using it with no apparent problems, but when I tried to play a video, I hit trouble.  First I opened it with Totem, which froze up and closed.  Then I tried VLC, and everything locked up.  The mouse moved slow and jerky for a few moments, but eventually stopped all together.  The keyboard didn't seem to respond and I couldn't switch to a terminal with Ctrl+Alt+F1.  I held the power button until the laptop shut down.  When I turned it on, I heard the ready sound that GDM makes, but the screen was black.  I switched to a terminal, changed to the nv driver in xorg.conf, and everything seems to work now, including the video.  But I want the features of the nvidia driver!  If I switch back to nvidia I get a black screen.  What gives?

If you ask me, that sounds like an nvidia driver problem/bug.  Try checking the resolution/refresh rates in /etc/X11/xorg.conf when nvidia driver is installed. Make sure you didn't set the resolution to high for your laptops monitor.

---

### Post by thetictacaddict on 2007-06-06
I checked the resolution and refresh rate to make sure.  The resolution is correct (it's the same one the nv driver uses anyway).  I commented out the refresh rates but I still get a blank screen with the nvidia driver.

---

### Post by thetictacaddict on 2007-06-06
Hoping to narrow down the problem, I booted the Reinstall Operating System option and did a reinstall to factory settings.  I booted up, installed the latest software updates, enabled the closed Nvidia driver using the restricted drivers manager, and restarted.  The splash screen looked good, but it was never affected by this problem.  As GDM started up, I once again heard the ready sound but saw only a black void.  The nv driver still works fine.

---

### Post by dmb on 2007-06-06
I think you may have a hardware problem, maybe your video card is broken on your new laptop. I would call up dell maybe.

---

### Post by thetictacaddict on 2007-06-06
Okay, go figure, it was something stupid.  I feel ridiculous now, but the problem is this: I had an external monitor plugged in, and the display was starting on that.  I didn't see because the monitor was set to a different input.  Of course, this doesn't explain the time everything froze up when I was playing a video, but I don't seem to be having that problem now so for now I will just hope it doesn't happen again.

I actually did call Dell, and once I got to the right person he was very helpful.

---


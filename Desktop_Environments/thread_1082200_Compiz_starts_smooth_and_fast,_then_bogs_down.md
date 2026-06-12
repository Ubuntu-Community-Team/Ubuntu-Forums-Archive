---
title: "Compiz starts smooth and fast, then bogs down"
date: 2009-02-27
forum: Desktop Environments
---

### Post by Mohonri on 2009-02-27
I just did a clean install of 8.10 on my Dell D600 laptop last night, and the radeon driver is working, and my desktop effects are enabled.

When I have no windows open (just a blank desktop), compiz runs like a dream.  It's smooth, it's pretty, and it's really fast.  However, as soon as I have any open windows, it bogs down really quickly.  It doesn't matter what the window is--nautilus, xterm, firefox.  As soon as I try any effect, the framerate goes down to the point where I can count the individual frames as the cube rotates.  If I close the window, the performance returns.

Is this a known issue?  Is there a fix?

Hardware:
Dell Latitude D600
Pentium M 1.4GHz
1GB RAM
Mobility Radeon 9000 (RV250)  (why, oh why did AMD discontinue their driver support? :( )

EDIT:  Looking on [the progress page](http://xorg.freedesktop.org/wiki/RadeonFeature) for the driver, there are several features which are still not complete.  I don't know if any of those would affect the performance in compiz, though.

EDIT more:  Lowering my resolution (to 1024x768 or 800x600) restores much of the performance.  However, why would there be such a difference from a clear desktop to a single window?

---


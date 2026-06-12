---
title: "Desktop monitor brightness dims on dark pages"
date: 2011-04-06
forum: Desktop Environments
---

### Post by vancouverite on 2011-04-06
Hello,
I have a problem that I haven't been able to solve by internet searches.  My desktop has a dual monitor with an GeForce GTS 240.  Everything seems to work perfectly, except for one annoying issue.  If I go to a dark page (like a website with a black background) the monitor that is displaying the dark image automatically dims.

The dimming only happens on the one monitor, but if both monitors show dark images they will both dim, independently.

I have tried all the stuff in nvidia-setting, and the command ```
nvidia-xconfig -A
``` gives a huge list of options but since I don't know the problem source, I don't know which option to look at.

Any ideas?

Thanks ahead of time.

---

### Post by Jeff Root on 2011-04-06
My first guess would be that the monitor is doing it.  If you look in
your monitor's settings you may find that it is set to "video" or
"multimedia" or some such, which may automatically reduce brightness
when most of the screen is dark, in order to reduce the amount of
light leakage which makes the black area look washed-out gray instead
of nice, deep, dark black.  So, try a different setting and see if it
changes the bahavior for the better.
 
   -- Jeff, in Minneapolis

---

### Post by vancouverite on 2011-04-07
Good call!  The monitor (a Samsung 226BW) has a "MagicBright" setting that is not accessible through the normal OSD. I downloaded the manual and found that it was set to "dynamic."  Setting it to custom solved the issue.

Thanks for the help!

---


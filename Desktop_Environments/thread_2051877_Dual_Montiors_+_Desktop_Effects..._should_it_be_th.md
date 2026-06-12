---
title: "Dual Montiors + Desktop Effects... should it be this hard to have both?"
date: 2012-09-02
forum: Desktop Environments
---

### Post by n8af on 2012-09-02
Hello fellow ubuntu guru's,

I was using Kubuntu Natty and had one hell of a time enabling desktop effects with dual monitors.  See this [thread]("http://ubuntuforums.org/showthread.php?t=1848634").  In the end, i was able to get it to work.

Now i've upgraded to Kubuntu 12.04 and the dual monitor + effects function stopped working.  In fact, I decided to do a fresh install of Kubuntu 12.04 to start from scratch.  

I've tried importing the settings from the thread link above.  This in fact made the problem worse.  The mouse was stuck at the left side of the screen and I could only move it up and down; in addition, the second monitor wouldn't enable after changing it to enable in the nvidia settings.  The only way I can get both monitors to work is by enabling both as X Screens and enabling Xinerama.

However, with Xinerama enabled, desktop effects are disabled and by going to settings -> desktop effects; it says they cannot be enabled.  I then read a thread where I can comment out the "Section Extentions", Option "Composite" "Disable" of the xorg.conf file.

Once I did this, the option to enable desktop effects is now open; however, even though I have it enabled, i get a task bar pop-up that pretty much says all the effects are still disabled.

Why is it so hard to have both dual monitors and desktop effects?

-Ive tried using proprietary drivers, and ubuntu's drivers; neither seem to make a difference.  

Any ideas?

Thanks,

-Nate

---

### Post by n8af on 2012-09-02
Nevermind - I was able to get it working by enabling twinview on both monitors within the nvidia settings.  For some reason it wasn't letting me enable twin view before - but now it is... may have something to do with switching drivers from proprietary to ubuntu's version.  Anywho, thanks to anyone who took the time to read this. :D

---


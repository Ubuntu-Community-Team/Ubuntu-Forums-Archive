---
title: "How to turn the desktop effects permanently on"
date: 2010-08-07
forum: Desktop Environments
---

### Post by zzzliperzzz on 2010-08-07
I'm using Kwin desktop effects. I turn on some desktop effects and it works
but after I reboot my PC, the desktop effects does not turn on automatically.
I always need to turn it on again. I always resume the compositing every restart.
Also, I can't find all the effects in kwin. I can only adjust the basic effects (the first tab) but when I tried to go to the all effects tab (the second tab) it is empty.
I hope someone can help me with this problem.
Thanks.

---

### Post by StephanG on 2010-08-09
Could you give us a bit more information?

What version of Kubuntu and KDE are you using?  Did you do a fresh install?  Or did you upgrade from Ubuntu or an earlier version of Kubuntu?

But from what you're describing, I can only guess that it is one of three things.

1)  You don't have the correct graphics drivers installed.   Check Application Launcer>> System>>Hardware Drivers.  It should tell you if the correct drivers are found/installed.  

But the fact that the effects can turn on at all means you must have some form of driver.  Perhaps you're using a free driver?

2)  Not all the necessary packages are installed.  I can only suggest you try to install the package kubuntu-desktop and see if that drags in the needed dependencies.

3)  You don't have enough RAM/CPU power.  If your system is low on resources, kubuntu might decide to disable desktop effects to lighten the load it places on your hardware.  What are your RAM/CPU specs?  There should be a plasmoid already installed that will give you the correct information.

Edit:  Are you using OpenGL rendering or XRender?  XRender isn't as mature as OpenGL and might cause a few problems.  But other than that, I'm out of ideas.  Maybe someone more knowledgeable could offer further insight?

---


---
title: "Problem installing RGL for R 3.2 in Ubuntu 14.04"
date: 2015-04-26
forum: Education &amp; Science
---

### Post by p-junkmail on 2015-04-26
I am running Ubuntu 14.04 (64 bot) and have  OpenGL support, X11 etc installed.
I am running R 3.2 and am trying to use RGL. This worked fine on my other installation 

I am able to install the RGL package without any error messages from CRAN using either R, RStudio or Ubuntu Synaptic Manager.

However when I open a 3d device using open3d() a device appears, but with corrupted contents.

I am able to use other programs that use the OPENGL such as Stellarium.

The following packages are all present.

mesa-common-dev
libglu1-mesa
libglu1-mesa-dev
freeglut3-dev

The machine is an HP ENVY with Intel Broadwell graphics
A previous similar installation on a MSI machine works fine with similar display resolution (1920x1080).

[ATTACH=CONFIG]261573[/ATTACH]

Any thoughts on how to fix this would be gratefully received.

Chris

---

### Post by monkeybrain20122 on 2015-04-26
Maybe the stock driver in Trusty is too old for Broadwell? Try to update your distro or the driver and kernel.

[http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY](http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY)

---

### Post by p-junkmail on 2015-04-30
Thanks. Updated and all sorted. Added Bumblebee at the same time so not 100% sure which bit solved the problem.

---

### Post by monkeybrain20122 on 2015-05-05
Bumblebee has nothing to do with it unless you have a optimus (switchable graphic) with a Nvidia card.

---


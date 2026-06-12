---
title: "AIGLX, XGL, Compiz all that good stuff..."
date: 2006-10-27
forum: Desktop Environments
---

### Post by statictonic on 2006-10-27
I just got finished upgrading to Ubuntu 6.10, I had installed XGL/Compiz on ubuntu 6.06, but uninstalled it after not to long since it was buggy.  Ubuntu 6.10 as far as I've heard has AIGLX, what exactly is that, and is it capable of doing anything similar to xgl/compiz?  Is any functionality like that built in?

---

### Post by ayoli on 2006-10-27
aiglx can do the same as xgl and is in xorg 7.1 (requires no particular install) you can use compiz or beryl (the compiz fork) with it, look here for some howtos:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu](http://wiki.beryl-project.org/index.php/Install/Ubuntu)

---

### Post by orb9220 on 2006-10-27
Yes xgl/beryl is xgl/compwiz just a different fork. And beryl can do more than compiz.

But you will have to install the beta drivers for your card. Like for nvidia are nvidia-9625 for ati ???. There are stickies like this one for nvidia. 

HOWTO: Beryl with latest nvidia drivers and EDGY's built in AIGLX (no XGL)
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

---

### Post by Charles Hand on 2006-10-30
> **statictonic said:**
> I just got finished upgrading to Ubuntu 6.10, I had installed XGL/Compiz on ubuntu 6.06, but uninstalled it after not to long since it was buggy.  Ubuntu 6.10 as far as I've heard has AIGLX, what exactly is that, and is it capable of doing anything similar to xgl/compiz?  Is any functionality like that built in?

AIGLX and XGL are both OpenGL implementations (thus they both have GL in the name) for X-windows (thus they both have X in the name). OpenGL is an API specification for graphics, especially 3D graphics. The difference between xgl and aiglx is, xgl is a hack of the xorg X server, while aiglx is a plugin to the xorg X server. Aiglx is generally considered more robust than xgl, and xgl is generally considered obsolete.

Compiz, which is now Beryl, does all it's 3D magic through an OpenGL api, be it implemented by xgl or aiglx.

I don't know about edgy, but on Dapper I think Nvidia people were able to get Beryl to work through xgl, and everyone else (including ATI and Intel) was able to get Beryl to work through aiglx. This is just my unscientific impression from forum posts.

---


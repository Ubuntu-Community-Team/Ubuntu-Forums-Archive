---
title: "opengl32 packages?"
date: 2006-03-04
forum: Gaming &amp; Leisure
---

### Post by Disastorm on 2006-03-04
I was trying to ./configure the 0.5 beta of PlanetPenguin Racer and it said I dont have opengl32 or mesa packages, how do I go about getting these?

---

### Post by jpkotta on 2006-03-04
I'm pretty sure mesa provides opengl (it's a software implementation of opengl).  But to get PPR to be playable, you'll need hardware accellerated opengl, so install the proper drivers for your hardware.  Mesa is available in the repos; you'll probably want libgl1-mesa-dev and libglu1-mesa-dev.  PPR is also in the repos in planetpenguin-racer*.  

In the future, if you're missing dependecies, just search in Synaptic for whatever you're missing and install the -dev package.  You might have to do a little trial and error.

---

### Post by Disastorm on 2006-03-06
I already have ATI drivers installed (that huge ati driver topic, also I get about 900 fps in glxgears -iacknowledgethistoolisnotabenchmark, and is there a search command for apt-get?

ppracer works (the apt-get one) for me.  The apt-get one is the non beta version though, but what is ppracer extras I got it but I dunno what it does?

---


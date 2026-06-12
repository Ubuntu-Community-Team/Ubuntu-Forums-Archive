---
title: "XPS M170 (7900 GTX GO) install with 7.10?"
date: 2007-10-24
forum: Dell  Ubuntu Support
---

### Post by shift1186 on 2007-10-24
Hey all.  I have tried a few other solutions and cant seem to get this to work.  First, i will post the system specs.

Dell XPS M170
Nvidia Geforce GO 7900 GTX (256mb, PCIe)

I downloaded the latest drivers from Nvidia (NVIDIA-Linux-x86-1.0-9755-pkg1.run).  These are what their page brought up for the 7900 GO.

I followed the instructions to the dot from this page:
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

EDIT:  Not really to the dot, since this was made on an old Ubuntu install and much older drivers.

Everything seems to install fine, except when i started GDM up again, i got the lovely black screen followed by the XConfig thing that says it didnt run correctly.  Luckly i was able to just copy the backup conf back and have a workable X session now.  But this doesnt help the situation.

I guess my question is what are the best drivers that someone has working with the 7900 GO GTX.  I am posting this in the Dell section since i know the dell GO card is different then the others.  For instance, i cant install the nvidia ones in windows.  I have to use the 2 year old dell drivers.  I even tried using the "hacked" nvidia INF files with no luck.

Thanks!

---

### Post by m94mni on 2007-10-24
I'm on gutsy, and there is no need whatsoever to use the nvidia installer. Just use the restricted drivers manager and you're done. That will give you the latest driver (1000.14.19).

FYI, I've had success with laptopvideo2go.com in Windows.

---

### Post by pbcartwright on 2007-10-24
install envy and let it configure your video card.. wonderful program!!
get it here:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Nunslaughter on 2007-10-25
don't use envy...

i have a xps m1710 with geforce go 7900 gs, and this card works just fine with the restricted drivers that ubuntu installs...you just have to look that ubuntu will install the nvidia-glx-new and not the nvidia-glx...

---

### Post by shift1186 on 2008-04-20
Well, i got the drivers working.. (LONG reply time eh?)

Now i have problems with dual monitor support.  I want to make my 37inch 1080p TV my primary, but cant seem to get it to display higher then 640x480... bah

---


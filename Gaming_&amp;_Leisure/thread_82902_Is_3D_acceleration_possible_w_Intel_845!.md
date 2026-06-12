---
title: "Is 3D acceleration possible w/ Intel 845?!"
date: 2005-10-27
forum: Gaming &amp; Leisure
---

### Post by remick182 on 2005-10-27
I'm just wondering if anyone knows whether or not 3D acceleration is possible to achieve in Ubuntu with my onboard Intel 845 graphics card.  I've tried the Nvidia drivers from a couple of different places - including the starter guides - and have no luck at all...I don't even get the supposed splash screen that you should get upon restarting X.  Am I wasting my time?

Thanks for your time.

---

### Post by matthew on 2005-10-27
[quote=remick182]I'm just wondering if anyone knows whether or not 3D acceleration is possible to achieve in Ubuntu with my onboard Intel 845 graphics card. I've tried the Nvidia drivers from a couple of different places - including the starter guides - and have no luck at all...I don't even get the supposed splash screen that you should get upon restarting X. Am I wasting my time?[/quote]
In short, yes, you are wasting your time. The nVidia drivers are only for use with graphics cards made by nVidia and they will not work with your Intel card (nor with my ATI card, etc.).

On the first question, I don't think 3-D acceleration is available for the onboard Intel 845, but if it is I'm sure some kind soul will post here and correct this statement.

---

### Post by shakin on 2005-10-27
I have acceleration on my i915 card, although it's still slow because the Intel cards aren't very good. I don't think it's any better on Windows.

You can try following my [old how-to for Hoary](http://ubuntuforums.org/showthread.php?t=27029), but check for a newer version of 855resolution than the one I posted. Run glxgears before and after installing the driver so you know if it helped at all. It certainly made my 2D faster, but it's still inadequate for 3D.

---

### Post by remick182 on 2005-10-28
I got an error when running glxgears:

[COLOR="Red"]Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual[/COLOR]

Am I missing something, or do I some incorrect settings?

---


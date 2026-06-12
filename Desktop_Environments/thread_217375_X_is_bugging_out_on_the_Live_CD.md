---
title: "X is bugging out on the Live CD"
date: 2006-07-17
forum: Desktop Environments
---

### Post by arcanistherogue on 2006-07-17
Hey, I tried to install Ubuntu 6.06 back when the RC was first released, and I remembered having problems with X.  I put my CDs somewhere when I got them, and now that I finally found them I decided to install Ubuntu Dapper 6.06.  However, when I boot up the Live CD, I hear all of the Ubuntu login noises and stuff however my screen is entirely covered in artifacts and random pixel patterns.  The sound still works though.   

I have a very old CRT monitor, it is a ViewSonic 17GS from 1996, and my video card is an nVidia 6600GT.  I tried doing sudo dpkg-reconfigure xserver-xorg however I still get the same results no matter what I put in, even if I turn the resolution all the way down.

I booted up into my old Ubuntu 5.10 install and then I got the information like refresh rates from the old xorg file, and then tried to manually put this into the xorg.conf file.  This didn't work, and I still got the same artifacts.

Does anyone know why this is happening, and how to get X to run properly?  It works on 5.10...

---

### Post by adam.tropics on 2006-07-17
> **arcanistherogue said:**
> 
I have a very old CRT monitor, it is a ViewSonic 17GS from 1996, and my video card is an nVidia 6600GT.  I tried doing sudo dpkg-reconfigure xserver-xorg however I still get the same results no matter what I put in, even if I turn the resolution all the way down.


Ignoring the resolution for a moment and just accepting default, did you also try different drivers, just to get you into X, maybe vesa? You probably did, just worth a mention!

---

### Post by arcanistherogue on 2006-07-17
Hmm... I haven't tried that yet.  I have just been using nv.  I will try it when I get the chance and post the result.

---


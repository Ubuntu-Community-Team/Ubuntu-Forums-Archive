---
title: "Problem With CompizFusion from guide"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by DuNuNuBatman on 2007-08-28
I followed the instructions from [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)
I ran though them twice just to be sure and I never received any error, but when I hit ALT+F2 and entered compiz --replace I didn't get anything. So I'm not sure what else I can do.

---

### Post by ayoli on 2007-08-28
try *compiz --replace* in a terminal, and post output here. give your grphic chip specs also.

---

### Post by Rupertronco on 2007-08-28
You have to make sure your system is configured for compositing, and you need to make sure your graphics drivers are up to date, also you have to check to make sure your 3d acceleration is enabled. 

Go to a terminal and type ```
glxgears
``` you should see 3 gears spinning around in your upper left hand corner. If you don't, you need to enable your 3d acceleration, if you do than we need to check your /etc/X11/xorg.conf to make sure it's configured correctly.

---

### Post by DuNuNuBatman on 2007-08-28
I thought I was doing something different by hitting ALT+F2 like in the article...
Anyway, I entered compiz --replace and I have the following output:

Checking for Xgl: not present.
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting

I missed the part about setting up x server on the parent site. Can I just install it now or will that affect what I've already done? Also, should I set up XGL, or AIGLX?

---

### Post by DuNuNuBatman on 2007-08-28
> **Rupertronco said:**
> You have to make sure your system is configured for compositing, and you need to make sure your graphics drivers are up to date, also you have to check to make sure your 3d acceleration is enabled. 

Go to a terminal and type ```
glxgears
``` you should see 3 gears spinning around in your upper left hand corner. If you don't, you need to enable your 3d acceleration, if you do than we need to check your /etc/X11/xorg.conf to make sure it's configured correctly.

Yup, I can see it. I've updated to the latest fglrx driver.

---

### Post by DuNuNuBatman on 2007-08-28
Never mind, I just noticed that AIGLX doesn't support my video card/driver ATI X1400 :(

---

### Post by ayoli on 2007-08-28
you need XGL for ATI cards, check out [this]("http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+fusion+ati")

---


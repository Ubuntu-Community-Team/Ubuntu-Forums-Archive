---
title: "nvidia-settings broke Xserver"
date: 2009-01-19
forum: General Help
---

### Post by skintythe1andonly on 2009-01-19
Hi

I was messing around with the resolution for my TV-out on my laptop. The last thing i changed was the settings from twinview to separate x servers... which required a xsever resart, on restart I get a blue screen saying Xserver cannot start. I can login to the commandline, if i try startx from there, it fails again saying

(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available

how do i correct this?.... Please help

I am using a nVidia Geforce 6150 Go btw.

---

### Post by bodhi.zazen on 2009-01-19
Sounds like you need to install the nvidia driver. 

Did you update your kernel ? If so, the nvidia driver needs to be re-installed with each kernel update.

---

### Post by skintythe1andonly on 2009-01-19
I had the nVidia driver installed.... had been using it for ages, it was only now I got fed up with the poor resolution on my TV I started messing with the nVidia-setting manager. I had not run a kernel update either.

Anyways I managed to fix it:)

I went into recovery mode and let it try and fix the xsever.

It managed to do so, but reset it without a nVidia driver I believe. When I went to login the first time it seemed ok until compiz tried to startup and then I got a while screen, so I figured I needed to disable compiz at startup. From a live CD i mounted my home and deleted the fusion icon in /media/disk/skint/.config/autostart/. I think I could have got away with doing it from another terminal but anyways.

I then re-installed the nVidia driver. All ok now so far.

---


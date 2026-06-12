---
title: "Webcam Scale Issues"
date: 2009-04-30
forum: General Help
---

### Post by gmike05 on 2009-04-30
I have a Mustek DV 3000 and running Ubuntu 9.04.  The webcam seems to work out of the box, but has a small bug.  When I use a program like Kopete or Gyachi, the webcam seems to crop the image or zoom into the middle.  It looks really strange to the person on the other end from what I have been told.  This only seems to happen when the webcam's resolution is 320 x 240.  A similar problem happens when I run cheese.  If I were to run cheese with resolution 480 x 464, the image is perfect, but as soon as I switch the resolution to 340 x 240 the webcam distorts the image the same way as gyachi and kopete.   My kernel is 2.6.28-11-generic and I have installed the latest libv4l package.  Any help, places I can look, or patches available?

---

### Post by loell on 2009-05-02
you really have to take the webcam issue on the webcam driver guys, if its gspca then got the spca guys or if its using a uvc driver then got the uvc devs.

---

### Post by gmike05 on 2009-05-04
Thanks for your response and I have the GSPCA driver and I found this bug report which pretty much describes this problem [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/93417](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/93417) .  It seems to have a patch, but not for Jaunty.  Anybody know of any workarounds?

---


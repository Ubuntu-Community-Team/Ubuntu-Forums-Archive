---
title: "gnome-shell graphics issues"
date: 2009-11-14
forum: Desktop Environments
---

### Post by aaronp on 2009-11-14
Hi guys,
I decided to try out gnome-shell and managed to get it to install/build successfully. However, when I fire it up it is 'almost' unresponsive (i.e. takes 5-10 secs to respond to any mouse events).
Cliking on Acitivites eventually brings up the side panel which looks fine but then choosing and app or launcher results in a white border around the screen after a few seconds and then after another few seconds, the icons (only) of my running apps appear in the main section.
I've also noticed that the icons in the notification area are just squares with 'static' looking graphic tears in them.

I'm guessing it has something to do with my graphics setup because it has similarities to issues I've seen with compiz in the past but I'm not sure what the issue is.

The terminal where I start it only shows this output:

```
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
```

Anyone have any suggestions or similar issues?

thanks
Aaron

---

### Post by aaronp on 2009-11-14
All, sorry disregard. I just realised since I installed Karmic that I hadn't installed the drivers for my card (since I decided not to bother with Compiz this time around)
I fired up EnvyNG, installed the driver and gnome-shell is working beautifully. I love it (so far, about 3 mins in!!)

---


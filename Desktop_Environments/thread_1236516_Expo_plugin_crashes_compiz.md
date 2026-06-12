---
title: "Expo plugin crashes compiz"
date: 2009-08-10
forum: Desktop Environments
---

### Post by bronkeydain on 2009-08-10
I have assigned mouse button 2 to activate Expo but I get the same problem when using Super-E keys. As soon as I activate Expo, Compiz crashes. I have tried starting compiz from the terminal (compiz --replace) and when it crashes it gives me this error message (nothing else):
```
Segmentation fault

```

I did check this thread but the problem there seems to be slightly different. 
[http://ubuntuforums.org/showthread.php?t=548543](http://ubuntuforums.org/showthread.php?t=548543)

Further I have never had this problem on previous releases of Ubuntu. Now after a clean install on an AMD XP2800 with Nvidia Geforce MX4000 I get this problem. I really really really want Expo to work!

---

### Post by bronkeydain on 2009-08-11
My system uses nvidia driver version 96, so I figured it was old and that might be the problem. I tried to install version 180 using this guide:
[http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/](http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/)

Only to find that my card is old and needs the old nvidia driver. As a result I have completely removed and reinstalled the version 96 driver.
My expo problem is still there. 

I  assume this problem is a bug. Does anyone have a workaround or tip to try next?

---

### Post by bronkeydain on 2009-08-14
bump

Gee, no response. Maybe someone can confirm if this is a bug or if this working for them?

---

### Post by bronkeydain on 2009-08-18
I have just upgrade to kernel2.6.28-15-generic and the Expo problem still exists :(

---


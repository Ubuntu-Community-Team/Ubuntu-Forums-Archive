---
title: "Much Needed Help Please"
date: 2009-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by newdellmini on 2009-05-22
I just installed the Ubuntu 9.04 on my dell mini 10. First off i tried downloading the flash player and it says error and how do i change my screen resolution? It only says 800x576... how do i change it back to the original from windows?? Overall whenever i do something or scroll through a page it seems pretty laggy... I think it might have to do with screen resolution. Any help?

Edit- I finally got the flash player to download after a couple updates. But how do i change my screen resolution to the normal on windows which is 1024x576. On ubuntu it wont let me change it from the 800x576.. there has to be some way.. Thanks!

---

### Post by sirebral on 2009-05-22
Maybe you have a broken package.  I am running 9.04 just fine.  Try running update manager to see if it can find any updates you missed.  You can also try System Testing.

---

### Post by Bucky Ball on 2009-05-22
You probably need to install the correct drivers for your graphics card/chip. What is it? NVidia, ATI? If you go to System->Administration->Hardware Drivers, is there a driver for the card? These drivers are third party, not open-source (although oepn-source ones do exist), not included with Ubuntu and MUST be installed post-OS install. Installing the appropriate driver, open-source or not, will regain your resolution settings through the driver's GUI.

Please use descriptive titles for your posts in future. :)

---

### Post by sirebral on 2009-05-22
Bucky Ball, It is a mini 9.  Intel GMA 950.  It should be Ubuntu ready.

EDIT: Oh shizz. It is a mini 10.  GMA 500.  Hrm  ....  Not sure how ready that is for 9.04 after all

---

### Post by Bucky Ball on 2009-05-22
> **sirebral said:**
> Bucky Ball, It is a mini 9.  Intel GMA 950.  It should be Ubuntu ready.


I'd be tempted to try Ubuntu Netbook Remix ...

Oh, and this

> **GMA 500**

 There is no sufficient driver support for the GMA 500. The driver wasn't developed in-house and will not work with kernels newer than 2.6.24. Newer distributions like Ubuntu 8.10 with a newer kernel will not work properly.
From here:

[http://en.wikipedia.org/wiki/Intel_GMA#GMA_500_2](http://en.wikipedia.org/wiki/Intel_GMA#GMA_500_2)

---

### Post by newdellmini on 2009-05-22
This might be not be the netbook remix. I thought that is what i downloaded.. 
Screen shot of my system
[IMG]http://img218.imageshack.us/img218/4797/screenshotnou.png[/IMG]

---

### Post by newdellmini on 2009-05-22
I tried downloading the video on ubuntu from dell. But it seems it wont install... Whats going on here?

---


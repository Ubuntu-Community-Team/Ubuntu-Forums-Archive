---
title: "video device not found? Dell Mini 9"
date: 2009-05-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CptSkippy on 2009-05-13
I've got a Dell Mini 9 with an integrated webcam.  It was working perfectly until I tried to install Netbook Remix.  After installing Netbook Remix, Wifi and Webcam disappeared.  It took me a while to find that I needed to add "wl" to the bottom of /etc/modules to get Wifi working again but I'm at a loss for the webcam.

If I use the lsusb command I can see the Webcam device but I have no idea how to tell if there is a driver associated with it.  Any help would be appreciated.

---

### Post by anjilslaire on 2009-05-13
Strange, U"ve been running both the 8.10 Netbook REmix and most recently the 9.04 UNR, and wifi & webcam both work out of the box.

Do you have the .3 megapixel or 1.3 megapixel camera? Perhaps there's a difference. I have the 1.3m

---

### Post by CptSkippy on 2009-05-14
> **anjilslaire said:**
> Strange, U"ve been running both the 8.10 Netbook REmix and most recently the 9.04 UNR, and wifi & webcam both work out of the box.

Do you have the .3 megapixel or 1.3 megapixel camera? Perhaps there's a difference. I have the 1.3m



I have the .3 megapixel camera.

Eveything worked great out of the box.  I downloaded and installed Skype using the .deb off Skype's website and it worked perfectly and immediately unlike some of the reports I've ready of Skype audio/video issues.

I'm considering just doing a system restore.  I uninstalled the Dell Video Chat application and some other packages that I didn't think necessary and I'm wondering if that's what broke it.

---


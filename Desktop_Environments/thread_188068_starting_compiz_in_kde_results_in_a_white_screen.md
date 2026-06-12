---
title: "starting compiz in kde results in a white screen"
date: 2006-06-03
forum: Desktop Environments
---

### Post by heretic9 on 2006-06-03
I followed the howto for xgl in the ubuntu wiki. When I launch compiz it results in a white screen with my only my mouse being displayed. The mouse moves and everything but I can't access anything, the screen is just white. 

I'm running kubuntu on an acer laptop with nvidia 7300.

---

### Post by heretic9 on 2006-06-03
oh and is there a way to tell if xgl is running? top doesn't show xgl but it doesn't show xorg either.

---

### Post by fifth on 2006-10-07
> **heretic9 said:**
> I followed the howto for xgl in the ubuntu wiki. When I launch compiz it results in a white screen with my only my mouse being displayed. The mouse moves and everything but I can't access anything, the screen is just white. 

I'm running kubuntu on an acer laptop with nvidia 7300.

I'm getting the same on gnome using the beta drivers from nvidia. Starting compiz results in a blank white screen. I can move the mouse to the top right and display a large grey/white window selector but nothing else is visible.

Would love to be able to get compiz working to have a play with it.

---

### Post by fifth on 2006-10-07
> **fifth said:**
> I'm getting the same on gnome using the beta drivers from nvidia. Starting compiz results in a blank white screen. I can move the mouse to the top right and display a large grey/white window selector but nothing else is visible.


Problem solved now - using Beryl instead and very happy.

Followed the guide at;

[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#beryl-manager_.28formerly_compiz-manager.29](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#beryl-manager_.28formerly_compiz-manager.29)

I think the fix for me was mainly due to the xorg server being update from the additional repos, although still the same version number and different copy.

So all is working well :D

---


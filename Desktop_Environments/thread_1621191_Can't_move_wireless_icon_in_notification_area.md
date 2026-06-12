---
title: "Can't move wireless icon in notification area"
date: 2010-11-14
forum: Desktop Environments
---

### Post by mattyu007 on 2010-11-14
The icons in the notification area became out of order when I switched displays (laptop / external display). I was able to rearrange all of them by right-click > Unlock from panel > Move except for the wireless icon which doesn't have a "Lock to panel" option when I right click it. Is there a way to move it back to the left of the date?

---

### Post by krishnandu.sarkar on 2010-11-14
It got messed up, delete the Wifi applet, and add it again.

---

### Post by mattyu007 on 2010-11-14
Sorry, I'm still relatively new to Ubuntu... so.. How do I delete the wifi applet (and add it back)?

---

### Post by mcduck on 2010-11-14
> **mattyu007 said:**
> The icons in the notification area became out of order when I switched displays (laptop / external display). I was able to rearrange all of them by right-click > Unlock from panel > Move except for the wireless icon which doesn't have a "Lock to panel" option when I right click it. Is there a way to move it back to the left of the date?

Your problem here is that there are actually many applets in that area, the Network Manager is the only in the Notification Area while all the others are completely separate applets.

So, to move the Notification Area-applet back to it's original place you need to unlock all the applets between it's current place and the desired location. The Indicator Applet (all the icons on the left), Clock Applet (clock & weather), Me-menu (the one with your user name) and Indicator-Applet-Session (the shutdown menu).

Another thing is that you can't access the Notification Area-applet's menu by clicking on the notification icons, that wold bring up the menu for the icon, not the applet. Instead you need to right-click on the small handle at the far left end of the applet. It's barely visible with the theme you are using, but there's a handle with three small dots between the Network manager icon and the shutdown menu. (same thing with the Window List-applet, by the way).

(and no, you definitely don't need to remove anything from your panel to do this, all the applets are movable.)

---

### Post by mattyu007 on 2010-11-14
> **mcduck said:**
> Instead you need to right-click on the small handle at the far left end of the applet. It's barely visible with the theme you are using, but there's a handle with three small dots between the Network manager icon and the shutdown menu.

Whoa I never saw that O_O Thanks a lot 8D Here, have some popcorn~ :popcorn:

---


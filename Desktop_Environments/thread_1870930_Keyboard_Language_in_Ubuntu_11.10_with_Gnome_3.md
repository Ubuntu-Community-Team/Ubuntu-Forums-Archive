---
title: "Keyboard Language in Ubuntu 11.10 with Gnome 3 ????"
date: 2011-10-28
forum: Desktop Environments
---

### Post by nedelkovskiv on 2011-10-28
Hi there i am running Ubuntu 11.10 with Gnome 3 ( i like the old look ) but i cant seem to find how to make visible which language my keyboard is on atm without having to click on the keyboard icon in the top right corner, i used to have this by default but ever since i switched to this new ubuntu and had to install gnome 3 , please if some of you can answer this i would be very thankful

---

### Post by fct on 2011-10-28
Try clicking on activities, search for "config" and launch "System configuration" in the search results. Then choose "Keyboard layout". There (2nd tab if I remember right) you can set the local layout.

---

### Post by crdlb on 2011-10-28
> **nedelkovskiv said:**
> Hi there i am running Ubuntu 11.10 with Gnome 3 ( i like the old look ) but i cant seem to find how to make visible which language my keyboard is on atm without having to click on the keyboard icon in the top right corner, i used to have this by default but ever since i switched to this new ubuntu and had to install gnome 3 , please if some of you can answer this i would be very thankful

This problem is related to Ubuntu's AppIndicator patches. They have modified GNOME to use an indicator instead of a tray icon, but there is no indicator-applet for gnome-panel 3.x in Oneiric. The result is that libappindicator provides a fallback tray icon that is inferior to the both real GNOME tray icon and to the Ubuntu indicator.

The bug for porting indicator-applet is: [https://bugs.launchpad.net/indicator-applet/+bug/724369](https://bugs.launchpad.net/indicator-applet/+bug/724369)

There now appears to be a PPA with a mostly-working port available: [https://launchpad.net/~jconti/+archive/gnome3/](https://launchpad.net/~jconti/+archive/gnome3/)

---

### Post by xslf on 2012-02-13
Hmmm... I installed the applet from the PPA, but gnome still seems to be using the fallback icon not giving me any indication to the active layout.

Other ideas?

Thanks!

---

### Post by xslf on 2012-02-13
Also- please ignore the version info in my profile- I have less than 50 posts so I'm unable to update it to the correct info.

---


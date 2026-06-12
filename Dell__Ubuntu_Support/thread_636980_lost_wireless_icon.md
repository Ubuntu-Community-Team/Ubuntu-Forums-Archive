---
title: "lost wireless icon"
date: 2007-12-10
forum: Dell  Ubuntu Support
---

### Post by ebsbox on 2007-12-10
when i initially installed ubuntu on my dell inspiron 6000 laptop, i had a wireless indicator icon on the top panel.  Clicking this icon listed all available wireless networks and allowed me to connect to any othem that i chose.

My problem is i accidentally removed the wireless indicator icon from my panel, now i don't know how to get it back.  any ideas?

---

### Post by saru411 on 2007-12-10
right click on the panel>add panel>system&hardware/network monitor

---

### Post by wormser on 2007-12-11
I have done this before and think this is one thing that needs to become more user friendly. You need to add Notification Area. Right click on the menu Panel and click Add to Panel.  If it still is not appearing then go to System> Preferences> Sessions. Look for Network Manager. Make sure it checked. If it not there then click add and use the following information.

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

---


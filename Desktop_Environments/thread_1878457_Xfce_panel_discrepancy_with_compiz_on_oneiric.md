---
title: "Xfce panel discrepancy with compiz on oneiric"
date: 2011-11-09
forum: Desktop Environments
---

### Post by Drone4four on 2011-11-09
Under compiz there is a discrepancy in how windows show up in expo workspaces and with how the same windows show up (or don’t show up) in xfce's workspaces in the panel.  Compare [this image]("http://picpaste.com/Toubleshooting_Xfce_and_Compiz_-_panel-GGcoOy1m.png") with [this image]("http://picpaste.com/Toubleshooting_Xfce_and_Compiz_-_expo-ZI9B3hiA.png").      The Xfce workspaces behave like they are completely broken when compiz is running.  How do I resolve this?   I experienced this glitch in natty.  I thought upgrading to oneiric would fix it but it didn’t since these pics were taken running Xubuntu 11.10.  

Also, how would I go about uninstalling compiz 0.9.x (development release) and installing 0.8.8 (stable release)?

---

### Post by 3Miro on 2011-11-09
Compiz workspaces work slightly different then the standard workspaces that you get with xfce or Gnome 2 or LXDE or KDE. There is always some discrepancy between the workspace applet and compiz. In your case in particular, this seems to be a problem with external monitors. I see similar stuff when I use xfce with xfwm4 (i.e. no compiz), then I get such discrepancy when I switch between different monitors. You can try to restart the workspace applet, but other than that I don't have a solution.

---


---
title: "Compiz Window Title Bar Below Top Panel"
date: 2012-08-10
forum: Desktop Environments
---

### Post by mamamia88 on 2012-08-10
Every maximized window the title bar shows up below the top panel while compiz is enabled.  I've already tried all the advice in this thread [http://ubuntuforums.org/showthread.php?t=1863179](http://ubuntuforums.org/showthread.php?t=1863179)   does anyone know of a fix for this very annoying situation? edit same situation on xfwm4 but changed the margin for top to be equal to panels number of pixels.  is there  a way to do something similar in ccsm?

---

### Post by Toz on 2012-08-10
Did you check that you referenced the correct panel?

```
xfconf-query -c xfce4-panel -p /panels/panel-0/disable-struts -t bool -n -s true
```
..."panel-0" refers to the first panel (panels are numbered starting at 0). If you have more than 1 panel, you'll have to change that to reference the correct panel. For example, the second panel (panel-1) should be:
```
xfconf-query -c xfce4-panel -p /panels/panel-1/disable-struts -t bool -n -s true
```

To find the panel number, right-click the panel, choose Panel->Panel Preferences.

---


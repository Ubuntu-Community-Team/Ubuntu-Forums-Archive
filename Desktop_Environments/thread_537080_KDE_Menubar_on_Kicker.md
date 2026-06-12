---
title: "KDE Menubar on Kicker"
date: 2007-08-28
forum: Desktop Environments
---

### Post by i-am-me on 2007-08-28
I want to put the menubar (the one that you can enable by right clicking the desktop and selecting current application's menu under the behavior tab of configure desktop) on the same panel as the kicker (i.e. the place where the taskbar used to be before I removed it) so that it's more like an OS X menubar. I've tried adding applets to the menubar and then setting kicker to disappear until the mouse is on some random corner of the screen, but there's no system tray. Is there a way move the system tray to the menubar or the menubar to the same panel as kicker?

---

### Post by ray bot on 2007-09-04
KDE only lets you have one system tray, so in order to add one to your menubar, you'll first have to remove it from your kicker panel.  Once you've done that, you should be able to add it to your menubar just like any other applet.

---

### Post by i-am-me on 2007-09-04
Oh thanks so much. I was wondering why.

---

### Post by i-am-me on 2007-09-05
After the whole thing that I did, kicker has become mostly unresponsive. I can't right click any panel for that menu, I can't open the Kmenu, can't open the trash, etc. The only things that work are the taskbar, system tray and menu on the menubar. Could this possibly be because I put a Kmenu on the menubar without removing the other first? Any way to unlock the panels from the command line and/or a command to remove one of the Kmenus if that's the problem?

---

### Post by ray bot on 2007-09-05
Adding a Kmenu to your menubar shouldn't cause kicker to hang. However, if you want to be sure, you can remove the Kmenu from your kicker panel with ```
dcop kicker Panel removeApplet Kmenu
``` Also, restarting kicker might bring it back to life. The command for that is ```
dcop kicker kicker restart
```

---

### Post by i-am-me on 2007-09-06
> **ray bot said:**
> ```
dcop kicker kicker restart
```

Thank you. that worked. I had previously been trying 
```
dcop kicker default restart
```

---

### Post by i-am-me on 2007-09-08
Oh it turns out that

```
dcop kicker kicker restart
```

was only a temporary fix for one session. 

```
dcop kicker Panel removeApplet Kmenu
```

fixed it for real this time.

---


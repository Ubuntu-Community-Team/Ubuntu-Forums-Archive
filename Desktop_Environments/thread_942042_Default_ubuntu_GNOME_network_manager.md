---
title: "Default ubuntu GNOME network manager"
date: 2008-10-08
forum: Desktop Environments
---

### Post by dur on 2008-10-08
What's the name of the little network applet that runs by default in the system tray in ubuntu's GNOME? I accidentally removed it from my toolbar and I'd like to have it back so I can easily manage my wireless networks.

Thanks!

---

### Post by UbuntuNerd on 2008-10-08
first you need to make sure you still have the area where the notification icons appear if you don't right click on top panel and press add to panel scroll down to notification area click on it and hit add then go to System> Preferences> Sessions Look for Network Manager and make sure is checked.
If is not there click add and enter this in the box

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

---

### Post by aysiu on 2008-10-08
Also check to see if you might have remove the Notification Area altogether and not just Network Manager's applet.

---


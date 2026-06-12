---
title: "missing system tray icons"
date: 2008-07-04
forum: Desktop Environments
---

### Post by zggame on 2008-07-04
I am using the XUbuntu 8.0.4LTS on a Dell Latitude C610 (PIII1.2G 512M). Last night, I accidentally click something like remove for the system tray network (nm-applet I think).  And it is gone, together with several other things there, such as the Date of Orgae and icons of programs like skype, pidgin, stardict....   Some native icons are still there in the panel, such as the network monitor, mixer, notes, cpu graph, time and quit button. I restart the system and restart the panel. Neither works.  I tried to run nm-applet and nothing shows up.  But if I ps -aux|grep nm-applet, I can see both the original one, nm-applet --sm-disable, and this new one I started.  similar for other programs like skype, pidgin, they are running fine, just fail to show up in he system tray. :confused: How do I get them back?  Thanks.

---

### Post by zggame on 2008-07-07
No one has any idea about this?

---

### Post by Vivaldi Gloria on 2008-07-07
In gnome, right click on an empty area of the panel, choose add to panel, then add sytem notification area.

Look something similar for xfce.

---

### Post by zggame on 2008-07-08
Here we go.  Thank you very much.  It works like a charm.  Thanks.

---


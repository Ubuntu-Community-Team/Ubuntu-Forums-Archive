---
title: "No display manager"
date: 2007-05-11
forum: Desktop Environments
---

### Post by KudouUsagi on 2007-05-11
I am trying to change my desktop manager from gdm to kdm so I edited the /etc/X11/default-display-manager to /kdm and restarted. Now it just loads to command line and I tried to type in /etc/init.d/kdm start and it tells me it wont start because kdm is not the default display manager and then when I type in /etc/init.d/gdm start it says it wont start because its not the default display manager either. What can I do to fix this and set kdm as the display manager?

---

### Post by aysiu on 2007-05-11
Your /etc/X11/default-display-manager file should say either ```
/usr/bin/kdm
``` or ```
/usr/sbin/gdm
``` What *exactly* does it say right now?

---


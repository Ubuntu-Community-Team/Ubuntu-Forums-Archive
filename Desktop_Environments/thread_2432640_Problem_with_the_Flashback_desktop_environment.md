---
title: "Problem with the Flashback desktop environment"
date: 2019-12-05
forum: Desktop Environments
---

### Post by danielsender on 2019-12-05
[HR][/HR]I am facing a problem on my Dell M70 running 18.04. I was running the Gnome Session Flashback with no problems. But after adding a new user, I cannot open the System Settings. Not only that, it appears that freezes the system to the point that I cannot shutdown nor reboot the system. I can do it only with the power button. I tried re-installing gnome-flashback, gnome-flashback-common and gnome-session-flashback but it didn't help. On the other hand if I logon under the Ubuntu desktop environment I can open the system settings and do everything.

Thanks

---

### Post by danielsender on 2019-12-06
I solved it by switching from gdm to lightdm, however I still don't know why gnome-control-center would not open after that operation. I will mark this as solved but I would have like to know what the issue was.

---


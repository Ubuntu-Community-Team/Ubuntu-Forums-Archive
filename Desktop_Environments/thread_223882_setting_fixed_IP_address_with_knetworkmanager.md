---
title: "setting fixed IP address with knetworkmanager?"
date: 2006-07-27
forum: Desktop Environments
---

### Post by holr on 2006-07-27
Hi,
   Im having fun with kubuntu, and really like the knetworkmanager tool for easily setting up my wifi in different locations. However, at work, I need to assign a fixed ip address and dns / gateway combo. How can i set this up in knetworkmanager? My normal way of doing it at the moment is to go to system settings and configure it in the network settings applet. Even though the internet is connected after this, knetworkmanager icon is still saying disconnected...

---

### Post by wieman01 on 2006-07-27
Basically you can't. (K)NetworkManager has two restrictions:

a. No static IP
b. No hidden ESSID

If you need either of them, try this:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

Hope this helps.

---


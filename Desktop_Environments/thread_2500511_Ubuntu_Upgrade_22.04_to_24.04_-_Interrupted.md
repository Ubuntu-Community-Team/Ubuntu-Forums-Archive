---
title: "Ubuntu Upgrade 22.04 to 24.04 - Interrupted"
date: 2024-09-04
forum: Desktop Environments
---

### Post by 13l-jason on 2024-09-04
I went to upgrade my system over the weekend as I do every time a new LTS version is available.  Go figure, we had a brief power outage in the middle of it.  System boots, and brings me to the desktop, but doesn't allow me to log in.  I get an error stating "Something went wrong" and tells me I must log out.  I can login to bash though, no issues there.  Once in there, when attempting to continue the update, it tells me I have broken packages.  I attempt the fix "apt --fix-broken install", it lists all the stuff it can't do and doesn't seem to actually do anything.  Networking isn't working.  When running ifconfig, I get the loopback, but no other interfaces.  I suspect that if I can get networking back online, I can probably get the packages fixed.  Recovery mode doesn't seem to help.

Any thoughts where to go from here?

BTW, I've been running this installation since 14.04, upgrading with each new LTS.  I'd hate to have to reinstall now.

Thank you

---

### Post by 13l-jason on 2024-09-04
I realized I posted this to the wrong group.  Sorry.  I've reposted to the appropriate group:  [https://ubuntuforums.org/showthread.php?t=2500540](https://ubuntuforums.org/showthread.php?t=2500540)

---


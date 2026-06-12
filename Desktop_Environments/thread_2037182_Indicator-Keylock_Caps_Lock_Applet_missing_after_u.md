---
title: "Indicator-Keylock Caps Lock Applet missing after upgrade 10.04 to 12.04"
date: 2012-08-03
forum: Desktop Environments
---

### Post by cy bais on 2012-08-03
Hi -

Sorry if previously posted, but I did search. I have indicator-keylock installed but it's not showing on my "Top Menu" next to the Battery, IM, Network, Logout etc. applets. It was there before my upgrade from 10.04 to 12.04.

Any ideas on how to get the CapsLock Applet to appear ?

Thanks in advance.

---

### Post by cy bais on 2012-08-04
Solved.

1. uninstall the indicator-keylock installed from 10.04

2. Add the indicator-keylock PPA found in the URL below

[https://launchpad.net/~tsbarnes/+archive/indicator-keylock](https://launchpad.net/~tsbarnes/+archive/indicator-keylock)

3. re-install using the above PPA with the version suited for Ubuntu 12.04

4. Run the indicator-keylock application from Launcher > Dash Home and the applet appears on the Task Menu (top).

---


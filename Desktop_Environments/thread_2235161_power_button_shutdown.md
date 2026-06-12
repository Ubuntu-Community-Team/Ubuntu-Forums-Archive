---
title: "power button shutdown"
date: 2014-07-19
forum: Desktop Environments
---

### Post by cmcanulty on 2014-07-19
I have several xubuntu 14.04 computers. All set in power manager to shut down via power button. When I do however the system sees it as improper shutdown and at next boot I get the black screen and have to click enter to start xubuntu

---

### Post by tgalati4 on 2014-07-19
Check the power management settings in BIOS.  Some computers have a 4 second delay which should be enabled when shutting down.  Others shut down immediately, which does not allow enough time to close files and syncronize the file system so that the disk is "clean" for the next boot.

In the 14.04 power management settings change the behavior of the power button to:  "Ask before shutdown".  This should bring up a dialog box asking the user to either Suspend, Shutdown, or Cancel.  This will then initiate a software shutdown instead of a hard shutdown.

---


---
title: "Making Emerald Defaut?"
date: 2007-04-28
forum: Desktop Environments
---

### Post by krazed nun on 2007-04-28
Is is possible to make emerald the default themer (rather than the normal one under prefrences), and if so, how can i do this?

Thanx in advance.:)

---

### Post by taurus on 2007-04-28
Emerald is for beryl.

---

### Post by RGCook on 2007-04-28
For Emerald to be loaded as default at boot, add the beryl-manager to your start-up programs in session manager as follows:

1. Click on System | Preferences | Sessions
2. Click on the Startup Programs tab to ensure it is active
3. On the right side of the box, click on New
4. In the name field, type Beryl Manager
5. In the Command field, type beryl-manager
6. Click on OK, and then Close.
7. To verify that Beryl's Emerald theme is now your default, log out and log back in (no need to to a full reboot). It should work.

---

### Post by JamaicaSka on 2007-05-01
Just saying thanks, this solved all my issues too :)

---


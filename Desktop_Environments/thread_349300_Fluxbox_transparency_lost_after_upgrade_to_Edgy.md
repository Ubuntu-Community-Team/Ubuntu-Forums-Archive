---
title: "Fluxbox transparency lost after upgrade to Edgy"
date: 2007-01-30
forum: Desktop Environments
---

### Post by gabng on 2007-01-30
Hi, I've downloaded fluxbox v1.0rc2 from [http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/), configured it with enabling imlib2 and disabling xmb options, and installed it on a clean dapper (6.06) server (no GUI) system.  The transparency of the menu and taskbar was working fine.  However after I did the dist-upgrade using aptitude, the transparency was lost.  I tried uninstalling, configuring and then installing fluxbox again, but nothing is transparent.  I couldn't find any topics regarding this issue in the forums.  Can someone help me out on this?

---

### Post by gabng on 2007-01-30
I found out the problem, I had to check the "Force Pseudo-Transparency" option under Configuration -> Transparency in the Fluxbox menu.  Upgrading to Edgy needed to have it checked for some reason.

---


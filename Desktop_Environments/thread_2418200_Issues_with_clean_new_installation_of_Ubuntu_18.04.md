---
title: "Issues with clean new installation of Ubuntu 18.04.2 LTS"
date: 2019-05-03
forum: Desktop Environments
---

### Post by hake2 on 2019-05-03
1. Chromium 74 has been released for more than a week but only Chromium 73 is available through Ubuntu software updater.  Actually, I did have Chromium 74 after I ran software updates on Ubunto 18.04.2 the first time I installed it but I did another install of Ubuntu on the same system and now Chromium stubbornly remains at version 73.

2. Ubuntu 18.04.2 LTS constantly reports 'System program problem detected'.  Apart from this irritant Ubuntu 18.04.2 behaves and works well on a Toshiba Satellite Pro P200 laptop.

---

### Post by kc1di on 2019-05-03
Hello hake2,
Welcome to Ubuntu.
You can get rid of the System fault report pop ups by following the instructions [here]("https://www.linuxbabe.com/ubuntu/disable-apport-error-reporting-ubuntu-16-04-lts").  (It's for 16.04 but works on 18.04 as well.)  

As far as the chromium upgrade goes, you will just have to wait until the package maintainers believe 74 is ready and bug free.  Or you can download chrome from their web page and install via software install.   There is also a Dev elopement branch[URL="https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev"] ppa 
here[/URL]. That has version 75 available , but this is beta release and may be buggy.  

My advise since your on the LTS release of Ubuntu is to wait and install the official chromium build and allow it to update when it's ready.  Unless there is some pressing need for the newer version.  Good Luck and enjoy :)

---

### Post by hake2 on 2019-05-04
Thank you **kc1di**. The instructions you pointed me to allowed me to disable 'apport' and the behaviour has ceased.

---

### Post by kc1di on 2019-05-04
your welcome enjoy :)

---

### Post by hake2 on 2019-05-04
Disabling, uninstalling and reinstalling (but re-enabling) **apport** seems to have much improved startup and shutdown.

---


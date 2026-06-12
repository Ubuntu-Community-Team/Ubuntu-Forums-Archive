---
title: "How can I fully return back to Unity 3D desktop?"
date: 2014-08-25
forum: Desktop Environments
---

### Post by Muneer_Shaheed on 2014-08-25
I've installed Ubuntu 14.04 and later installed Mate desktop environment. I did not like it and wanted to switch back to Ubuntu Unity. I removed Mate Desktop from the system also. But I have several issues.

* Loading screen while booting shows Ubuntu-Mate background.
* Login screen still the same as of Mate
* 2 Network icons at top bar

[IMG]http://i61.tinypic.com/1j4005.png[/IMG]

* Little slower than before to load the whole desktop after pressing <ENTER> putting password on login screen.

Please help me get back to original Ubuntu.

---

### Post by ajgreeny on 2014-08-25
If you installed mate as a single operation, ie not with lots of other packages that you wanted, you can find all the packages that were part of the mate installation by looking at the output of ```
grep -iw install /var/log/dpkg.log.1/var/log/dpkg.log
``` which will show a list like 
```
/var/log/dpkg.log.1:2014-07-23 20:25:26 status triggers-pending install-info 4.13a.dfsg.1-8ubuntu2
/var/log/dpkg.log.1:2014-07-23 20:25:33 trigproc install-info 4.13a.dfsg.1-8ubuntu2 4.13a.dfsg.1-8ubuntu2
/var/log/dpkg.log.1:2014-07-23 20:25:33 status half-configured install-info 4.13a.dfsg.1-8ubuntu2
/var/log/dpkg.log.1:2014-07-23 20:25:33 status installed install-info 4.13a.dfsg.1-8ubuntu2
/var/log/dpkg.log.1:2014-07-30 11:34:22 startup archives install
/var/log/dpkg.log.1:2014-07-30 11:34:25 install sphere-icons <none> 1.25.3~precise~NoobsLab.com
/var/log/dpkg.log:2014-08-04 11:37:48 install lynx-cur <none> 2.8.8dev.9-2ubuntu0.12.04.1
/var/log/dpkg.log:2014-08-05 22:14:19 install xpad <none> 4.0-5ubuntu2
/var/log/dpkg.log:2014-08-06 10:37:47 status triggers-pending install-info 4.13a.dfsg.1-8ubuntu2
/var/log/dpkg.log:2014-08-06 10:37:47 trigproc install-info 4.13a.dfsg.1-8ubuntu2 4.13a.dfsg.1-8ubuntu2
/var/log/dpkg.log:2014-08-06 10:37:47 status half-configured install-info 4.13a.dfsg.1-8ubuntu2
```
You can see the date and time near the start of each line which will help you find all the packages installed at the same time, ie your mate DE packages, and will allow you to remove them all, which should get you back to where you want to be.

---


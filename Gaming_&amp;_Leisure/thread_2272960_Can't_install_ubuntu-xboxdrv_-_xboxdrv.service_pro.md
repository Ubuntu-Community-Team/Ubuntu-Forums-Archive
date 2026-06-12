---
title: "Can't install ubuntu-xboxdrv - xboxdrv.service problem"
date: 2015-04-09
forum: Gaming &amp; Leisure
---

### Post by mao_dze_dun on 2015-04-09
Hi, guys. I have been trying to install ubuntu-xboxdrv for some time now but alas I get the following error - Failed to start xboxdrv.service: Unit xboxdrv.service failed to load: No such file or directory. It's extremely irritating. I tried manually putting a dummy file in there and applying all permission but then it said that the file was masked. Does anybody have an idea what can be done?

---

### Post by ajgreeny on 2015-04-09
I have occasionally had that error at start of VBox after an update to the VBox application, which is direct from Oracle, but in my case the error always has told me to run command ```
sudo /etc/init.d/vboxdrv setup
``` to solve the problem.  It worked without a problem and my VBox worked fine after that.

---


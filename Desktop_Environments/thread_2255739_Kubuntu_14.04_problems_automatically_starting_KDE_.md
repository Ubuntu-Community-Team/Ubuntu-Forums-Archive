---
title: "Kubuntu 14.04: problems automatically starting KDE after booting..."
date: 2014-12-07
forum: Desktop Environments
---

### Post by trancephorm on 2014-12-07
After recent update, one problem emerged: after the reboot, Kubuntu 14.04 won't automatically start KDE, it just gives me console login in text mode. I recall having some problem with last upgrade of the system... Last lines were some errors.

Still, when I login and sudo reboot, booting for the second time works - loads KDE automatically.
How can I troubleshoot this problem, I guess there are some log files involved...

Thanks.

---

### Post by Rob Sayer on 2014-12-07
I'd try booting temporarily using the nomodeset parameter first.  See:

[http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

---

### Post by trancephorm on 2014-12-07
Thanks... I just did "sudo update-grub" and it seems it's fixed now.... It booted normally in GUI, will reply back to this thread if this was actually not the fix.

---


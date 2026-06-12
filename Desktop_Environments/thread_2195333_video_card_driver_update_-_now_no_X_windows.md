---
title: "video card driver update - now no X windows"
date: 2013-12-23
forum: Desktop Environments
---

### Post by levensondavid on 2013-12-23
Hey all,
I just updated my nVidia drivers on my Kubuntu 13.10 installation.  Now my system will not boot into the GUI.  I've tried reinstalling lightdm, but that did not work.  I've tried uninstalling the nVidia drivers, but that seems to have had no positive effect.  Please let me know what additional info you need to be so we can work toward a solution to this issue.
Thanks,
David

---

### Post by levensondavid on 2013-12-23
update... tried removing and reinstalling lightdm.  no change.  Same issue

---

### Post by levensondavid on 2013-12-23
UPDATE - ran the following command 

sudo apt-get remove nvidia*

After reboot, I was returned to an X windows interface and GUI login.  WOW.  linux for me is still a work in progress.  Although it's been my primary home OS for almost four years, it's been very resilient, and this is the first time I thought I was going to be reinstalling to recover.  This was a good learning experience.  I hope the command above helps someone else out of a jam.

---

### Post by deadflowr on 2013-12-24
Here's some helpfulness for nvidia
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---


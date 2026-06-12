---
title: "Replace GDM with SLIM?"
date: 2010-04-22
forum: Desktop Environments
---

### Post by AndyBoy_LV on 2010-04-22
Hi!

I`m using Xubuntu 9.10 and really want to replace the GDM with SLIM. I installed it, i can run it by switching to tty1 and stopping GDM ```
sudo /etc/init.d/gdm stop
``` and starting slim ```
/etc/init.d/slim start
``` It works ok, i can login and start my XFCE session from there. I changed my default manager from GDM to Slim by running ```
sudo dpkg-reconfigure slim
```. But when i reboot my computer, the booting process stops at the point when it has to launch GDM (or Xsplash? Not really sure how the whole process works). When i revert back to GDM being my default manager, everything works fine. Any suggestions? Has anyone accomplished this before?

---

### Post by pevzi on 2010-04-23
The same thing on Ubuntu 10.04.

---

### Post by AndyBoy_LV on 2010-04-26
This all reminds me of one joke... 

What`s the difference between an advanced Ubuntu user and advanced Gentoo user? Advanced Gentoo user can always answer avanced ubuntu user questions, but not vice versa :))

---

### Post by eev2 on 2010-06-06
What's in /etc/X11/default-display-manager ?

---


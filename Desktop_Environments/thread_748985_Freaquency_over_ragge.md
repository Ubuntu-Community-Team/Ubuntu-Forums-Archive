---
title: "Freaquency over ragge"
date: 2008-04-08
forum: Desktop Environments
---

### Post by asliyanage on 2008-04-08
i installed ubuntu 7.10 to my machine.now there are ubuntu and windows xp.when i loging to ubuntu there is a message freaquency over range.after few seconds loging window is coming.what is the problem.but when i using ubuntu 7.04 there wasn't such a problem.

---

### Post by asliyanage on 2008-04-08
hi

---

### Post by russo.mic on 2008-04-08
sounds to me like you've got xorg.conf setup wrong.  THe frequency range in xorg.conf is such that your monitor isn't able to display the signal.  

Do this from a failsafe terminal:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup

sudo dpkg-reconfigure -phigh xserver-xorg

Good Luck!

Russo

---


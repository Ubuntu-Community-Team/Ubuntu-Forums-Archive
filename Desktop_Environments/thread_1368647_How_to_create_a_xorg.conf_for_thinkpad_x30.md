---
title: "How to create a xorg.conf for thinkpad x30?"
date: 2009-12-30
forum: Desktop Environments
---

### Post by alphachoi on 2009-12-30
i had install xubuntu 9.10 and something wrong about display.

How can i create a correct xorg.conf?

thanks all for your help

Alpha.

---

### Post by lorsen on 2010-01-13
I found one for Xorg 7.1 (gentoo): [http://www.onderka.com/wp-content/uploads/2006/11/xorg.conf_x30](http://www.onderka.com/wp-content/uploads/2006/11/xorg.conf_x30)
But I really have no idea if that will help ...

---

### Post by FlyingBuzz on 2010-01-14
Try to run
sudo X -configure
It will create a new xorg.conf file in your /root directory. Then backup your current xorg.conf, replace with the new one. Then reboot or restart X to see the effect.

---


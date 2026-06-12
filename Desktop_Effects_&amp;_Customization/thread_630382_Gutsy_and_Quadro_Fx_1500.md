---
title: "Gutsy and Quadro Fx 1500"
date: 2007-12-03
forum: Desktop Effects &amp; Customization
---

### Post by robert_ps88 on 2007-12-03
hi, i have recently installed ubuntu gutsy. ihad a problem with my graphic cards. its quadro fx 1500, after the gutsy just installed it worked fine with "nv" driver but when i tried to activate the full desktop effect it asked me to install the nvidia restricted driver. i tried but it give me a very low resolution (640X480) and thre is nothing i can do. it worked again when i disabled the restricted driver.

any help would be appreciated thanks.

---

### Post by messybricks on 2007-12-03
I'm not sure if that graphics card is supported by the restricted driver, but you can try this:

somehow get into a terminal (CTRL-ALT-F1 while logged in should work, otherwise, you can go into recovery mode)

sudo dpkg-reconfigure xserver-xorg

select the "nvidia" driver, and ignore all the other screens that will come up (just hit OK), until you get to one that shows a bunch of different resolutions.  Use the spacebar to select the resolution(s) that you want (make sure it's no more than your monitor's maximum resolution).

when you're done, do

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

---


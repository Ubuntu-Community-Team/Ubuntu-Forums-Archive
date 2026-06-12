---
title: "just upgraded from 5.04, need help!!"
date: 2005-11-11
forum: Desktop Environments
---

### Post by cooldudejz on 2005-11-11
ok, so today i just upgraded from 5.04, i did sudo apt-get dist-upgrade, everything was working well, then i restarted and my xserver-xorg didnt work, so i ran dpkg-reconfigure xserver-xorg and tried to fix it. once i choose 24 bit color i get this 
"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.200511111238"
so i thought the process was over, i restart and it still says my xserver-xorg is not configured right. can anyone help me, i really dont want to do a fresh install, i know there is a way to fix this, but i am kinda new to ubuntu. thanx

---

### Post by Kyral on 2005-11-11
Were you using the ATI or NVidia Accelerated Graphics drivers by any chance?

---

### Post by cooldudejz on 2005-11-11
yes i was using the NVidia Accelerated Graphics driver

---

### Post by Kyral on 2005-11-11
You have to reinstall it. Breezy uses a new kernel and the Kernel Module for NVidia GLX from Hoary doesn't work with the Breezy Kernel

---


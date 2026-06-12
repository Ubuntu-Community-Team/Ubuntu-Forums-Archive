---
title: "Screen order reversed Ubuntu 14.04"
date: 2014-08-23
forum: Desktop Environments
---

### Post by Robbyx on 2014-08-23
I am using the gnome 3? desktop on Ubuntu 14.04. Apart from the absence of minimise and maximise window buttons I am very pleased with it.

I use two monitors. I can reset them to the correct positions using nvidia xserver or the display setting, but they only stay the right way round until the next reboot.

Am I right that gnome is using xorg.conf?

Nvidia xserver gives the option to save the changes but does not open in the right place. What is the correct location for xorg.conf,  if that is the file that needs modifying?

```
robins@robins-EP35-DS3L:~$ whereis xorg.conf
xorg: /usr/lib/xorg /usr/include/xorg
robins@robins-EP35-DS3L:~$ 

```

---

### Post by bizhat on 2014-08-23
xorg.conf is located in folder /etc/X11

---

### Post by Robbyx on 2014-08-23
Thank you. It was not there so I created it with the nvidia-server settings file and I have the screens working properly now.

---


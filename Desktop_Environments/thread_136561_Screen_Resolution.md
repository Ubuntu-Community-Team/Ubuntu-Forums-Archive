---
title: "Screen Resolution"
date: 2006-02-26
forum: Desktop Environments
---

### Post by swooshvapors13 on 2006-02-26
My screen is 640 by 480 pixels when the last time I logged in it was 1040 by 780. I cannot change the resolution by going to the screen resolution section of the system>preferences menu and I cannot change it by using the monitor. please help!

---

### Post by BeatBoxRocker on 2006-02-26
Could you paste the section Screen located in /etc/X11/xorg.conf? Maybe you should add some parameters in that section to be able to increase desktop resolution.

Saludos!

---

### Post by swooshvapors13 on 2006-02-26
I am new at all this and I have no idea how to set parameters:(

---

### Post by bluevoodoo1 on 2006-02-26
in a terminal (accessories > terminal) type

gedit /etc/X11/xorg.conf

and copy everything (right click select all) and paste the contents here.

you can use

sudo dpkg-reconfigure xserver-xorg

do reconfigure your video too.

---


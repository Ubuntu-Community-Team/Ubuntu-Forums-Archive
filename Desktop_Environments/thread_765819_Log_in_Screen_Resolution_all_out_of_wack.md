---
title: "Log in Screen Resolution all out of wack"
date: 2008-04-24
forum: Desktop Environments
---

### Post by Justin Holt on 2008-04-24
Hi all,
I just upgraded from Gutsy to Hardy by changing all the sources and updating them and then proceeding to use dist-upgrade in the terminal. My problem comes where when the computer first boots up. The log in screen is ridiculously large and only shows the upper left corner. Something tells me that the screen resolution is too high and my monitor is only displaying what it actually can. I have an nVidia 6600 GT with the latest drivers if that helps any bit.

Thanks again, 

Justin

---

### Post by Justin Holt on 2008-04-26
Turns out one of my friends on AIM had the same problem and he helped me fix it. All I had to do was boot to recovery mode and had to reconfigure X.

sudo dpkg-reconfigure -phigh xserver-xorg

and then reboot.

Hope it helps people as it did for me!

Justin

---


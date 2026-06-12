---
title: "xorg help!!"
date: 2007-03-25
forum: Desktop Environments
---

### Post by giambrone on 2007-03-25
Hey guys - I think I saw this somewhere on the forums - but I can't find it again!
I just ran apt-get upgrade -c -d and upgraded my kernel, but after the ubuntu bootloader GDM and xserver doesn't start up - I'm left at the terminal thing. Wondering if its a driver issue?
I can't get to that computer at the moment - was wondering if a quick> *sudo dpkg-reconfigure xserver-xorg* would do the trick...

Any help much appreciated

Matt:KS

---

### Post by louis_nichols on 2007-03-25
The quickest way would be:
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```
The driver for your video card should have been upgraded with your kernel. Else, you'll have to do it yourself and then run the xconfig utility that comes with your driver.

---

### Post by giambrone on 2007-03-26
Thanks :) - I'll give it a go when I'm back from school
Will reply if it doesnt work...

Matt:KS

---

### Post by giambrone on 2007-03-26
Yay - It worked, it was the nVidia driver, and so I used the vesa one. Just have to reinstall the latest nVidia one now :)

Matt:KS

---


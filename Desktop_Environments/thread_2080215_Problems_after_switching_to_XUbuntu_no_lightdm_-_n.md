---
title: "Problems after switching to XUbuntu: no lightdm - no shutdown - no removable drives"
date: 2012-11-03
forum: Desktop Environments
---

### Post by bwinfrey on 2012-11-03
Hello all,

I was having some issues with opengl in ubuntu-desktop, so I removed it and installed xubuntu desktop.  

* lightdm wont start after replacing ubuntu-desktop with xubuntu-desktop

Since then the graphical login does not start.  If I start it manually an it stops at checking battery (desktop), and I have to use startx to start X.  I have tried 
'dpkg-configure lightdm'
'apt-get -f install'

I installed xdm, which gave me a chooser to select the dm, and I chose lightdm.  Still no luck

cat /etc/X11/default-display-manager 
/usr/sbin/lightdm

* cant shutdown without using three finger salute.

* cant (un)mount/eject removable usb storage

I did fix the opengl issue by using x-swat repo nvidia current and running jockey as root.  So that's something anyway.

Any help is appreciated.

Thank you.

Regards,
Brian

---

### Post by mike555 on 2012-11-03
Sounds like you didn't do a new clean install of Xubuntu, that is what you should do so you don't have left-over stuff.....

---


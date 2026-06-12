---
title: "Mouse and keyboard doesn't work at ubuntu 8.10 server"
date: 2009-05-01
forum: Desktop Environments
---

### Post by 8200 on 2009-05-01
Hi guys.


I have got a pretty old notebook on which I have successfully installed  ubuntu 8.10 desktop (without having any problems).

But it was very slow so now I have installed ubuntu 8.10 server and "xorg fvwm-crystal msttcorefonts". I have added the line "fvwm-crystal" to ~.xinitrc and finally entered "startx".
Fvwm-crystal loads but neither the mouse or touchpad nor the keyboard works.


I have already successfully installed ubuntu 8.10 server + fvwm-crystal on another pc in the exactly same way.


:confused:


Thanks!

---

### Post by 8200 on 2009-05-01
It's not a problem of fvwm-crystal because now I have installed xdm, started it and also can't move to the mouse or enter username+pw.

---

### Post by 8200 on 2009-05-01
Here you can see the xorg log file:

[http://pastebin.com/f7141fba](http://pastebin.com/f7141fba)

---

### Post by 8200 on 2009-05-01
Finally I have found the missing thing: hal


"sudo apt-get install hal" solved my problem :)

---


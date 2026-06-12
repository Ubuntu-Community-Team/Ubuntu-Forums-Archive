---
title: "Wanting to install JWM Correctly"
date: 2008-05-10
forum: Desktop Environments
---

### Post by mikeyc6534 on 2008-05-10
I have Ubuntu 7.10 wanting to make JWM my permanent window manager. I would to install JWM then remove Gnome and all it's dependencies. What would be the safest and best way to do this? Also, would Xen work with JWM? If so, could anyone help me set that up after I get JWM installed?

---

### Post by kerry_s on 2008-05-10
sudo apt-get install jwm menu
sudo update-menus
optional:
cp /etc/jwm/jwmrc ~/.jwmrc
log out, select jwm in the session menu and log in.

to remove gnome you'd have to hunt down all the gnome stuff, better to start from a base install and build up. recommend just leaving it for now.

xen will work fine, any program you run in any other de will work exactly the same in jwm.
sorry, i've never used xen, so->
[http://www.howtoforge.com/perfect_xen_setup_debian_ubuntu](http://www.howtoforge.com/perfect_xen_setup_debian_ubuntu)

let me know if you need anything else. i'm one of the few jwm users around here. :) i build mine up from debian though.

---

### Post by mikeyc6534 on 2008-05-11
Thanks I found out how to remove the gnome desktop on Ubuntu so I am good to go.

---


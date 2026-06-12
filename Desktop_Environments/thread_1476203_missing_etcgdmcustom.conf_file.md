---
title: "missing /etc/gdm/custom.conf file"
date: 2010-05-07
forum: Desktop Environments
---

### Post by dbclinton on 2010-05-07
I just installed Edubuntu 10.04 and I've experienced a number of crashes (screen goes black, then strange color schemes, and then a reboot). The system logs all mention variations of:

gdm-simple-slave[1655]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory

In fact, there is no custom.conf file in /etc/gdm/
I tried reinstalling gdm from synaptic and sudo dpkg-reconfigure gdm, but with no success. How should I create a custom.conf file and what should it contain?
Thanks,

---

### Post by Nickjpost on 2011-01-28
Bump

---

### Post by Krytarik on 2011-01-28
Although I don't why the file is missing, this manual may help to create one:
[http://library.gnome.org/admin/gdm/stable/configuration.html.en#daemonconfig](http://library.gnome.org/admin/gdm/stable/configuration.html.en#daemonconfig)

This is the content of my custom.conf:
```
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=krytarik
AutomaticLogin=krytarik
TimedLoginDelay=30
DefaultSession=gnome
```

---


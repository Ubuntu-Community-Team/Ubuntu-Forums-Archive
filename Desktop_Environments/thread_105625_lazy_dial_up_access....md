---
title: "lazy dial up access..."
date: 2005-12-18
forum: Desktop Environments
---

### Post by mjshepherd on 2005-12-18
I've finally managed to get my internal (conexant) modem and dial-up access to allow me access to the internet through ubuntu (using a downloaded driver from linuxant, and using pppconfig, rather than the networking accessory under the admin menu).  This means i'm dialling up with "pon" and logging off with "poff" at the command line.  However, is there a simple graphic version (say a button on the desktop) that i can download which will do the same thing, and perhaps give me an idea of my dialup status (verifying password etc.), and maybe even let me know how long i've been online?

Cheers!  Matthew

---

### Post by adwait on 2005-12-18
There's gppp and kppp for Ubuntu and Kubuntu respectively. To install them,
```
sudo apt-get install gppp
```
or
```
sudo apt-get install kppp
```

---

### Post by mjshepherd on 2005-12-18
Thanks!

I tried this and got:

Reading package lists... Done
Building dependency tree...Done
E: Couldn't find package gppp

What am i doing wrong?

---

### Post by migueljacq on 2005-12-19
I'm wondering if it should've been 'gnome-ppp'?

---

### Post by adwait on 2005-12-19
Yup sorry, should have been gnome-ppp
```
sudo apt-get install gnome-ppp
```

---

### Post by mjshepherd on 2005-12-19
well... gnome-ppp resulted in the same problem occurring.  Maybe this is because the home website for this programme closed in may ([www.gnome-ppp.org)](www.gnome-ppp.org)).  However, after a google search i was able to download it from as a debian package, and install it.

Thanks everybody!

Matthew:p

---


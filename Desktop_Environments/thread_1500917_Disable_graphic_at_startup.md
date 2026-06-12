---
title: "Disable graphic at startup"
date: 2010-06-03
forum: Desktop Environments
---

### Post by rt-2 on 2010-06-03
Hi,
I have installed ubuntu-desktop via
```
apt-get install ubuntu-desktop
```
but i don't want it to start at the boot....

I tried :
sudo apt-get remove usplash -> it's not installed
sudo apt-get remove ubuntu-desktop -> it still start with graphic, but in a lower process(don'T remeber what it said)
update-rc.d -f gdm remove it still open

and theres no process on /etc/rc2.d/ thats contain gdm in its name...

Thank you...

---

### Post by lukeiamyourfather on 2010-06-03
I'm also curious about this. In past years I've just set the default runlevel to 2 or 3 instead of 5, but it doesn't seem to make any difference in Ubuntu Server after installing the ubuntu-desktop package.

---

### Post by rt-2 on 2010-06-04
i'm new to ubuntu...:confused:

---


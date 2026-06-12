---
title: "Starting GNOME Display Manager... [fail]"
date: 2007-12-27
forum: Desktop Environments
---

### Post by michaelgod5 on 2007-12-27
I was trying to install AWN(Avant Window Navigator) today and I've modified glib-gettext and libglib2.0-dev

After reboot 
Starting GNOME Display Manager... [fail]

..:(:(:(

sudo apt-get install --reinstall gdm

sudo apt-get install --reinstall gdm gnome xserver-xorg
In addition,these two commands are useless. 

Please help me!

---

### Post by dvijaydev46 on 2007-12-27
You can try this:

sudo aptitude update
sudo aptitude install ubuntu-desktop

and then type:

sudo /etc/init.d/gdm start

It should work

---

### Post by michaelgod5 on 2007-12-27
Uh,.. It doesn't work

---

### Post by p_quarles on 2007-12-27
Are you getting any further information about the source of the problem when you run the /etc/init.d/gdm start command? If that's not giving you any information, I would look at the log files in 
```
/var/log/gdm
```
for further information. 

Also, since you mentioned that you tried modifying a couple of major libraries, you might want to try to reset those:
```
sudo dpkg-reconfigure glib-gettext 
sudo dpkg-reconfigure libglib2.0-dev
```
Finally: did you add AWN to the session startup routine? If not, I think it's safe to say that AWN is not the problem, rather it's something that was done during the process of installing it.

---


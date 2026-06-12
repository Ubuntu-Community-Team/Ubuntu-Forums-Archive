---
title: "Changing Default login screen"
date: 2011-01-09
forum: Desktop Environments
---

### Post by navyjosh on 2011-01-09
Hi, I'm a really big newb.  I barely know anything about linux or Ubuntu.  I recently installed 10.10 and I used the command

```
sudo apt-get install xdm
```

and it changed my login screen and a few passwords that Ubuntu has remembered in the past such as my WPA password for my network.

I was wondering if there was a quick and easy way to change my login screen back to the default that came with the OS and undo this install xdm.

I also used this code, which may have done it:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```
Thanks,

I realize this is a flamingly newbish question.

---

### Post by pavi_elex on 2011-11-08
$ 
sudo update-rc.d xdm disable
$ /usr/bin/update-rc.d -f xdm remove
$ sudo dpkg-reconfigure gdm

---


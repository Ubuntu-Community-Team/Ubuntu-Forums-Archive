---
title: "XFCE on Ubuntu server?"
date: 2014-10-20
forum: Desktop Environments
---

### Post by guldberg72 on 2014-10-20
Hello guys. i was wondering if it is possible to install xfce on ubuntu server so i have the option to start and stop the grapichal gui ? and when i boot up my server it is automatic turned off and needed to be startet from the shell before it appears?

---

### Post by ian-weisser on 2014-10-20
[Edit] Bucky Ball (below) said it better than I did.

---

### Post by Bucky Ball on 2014-10-20
DON'T install xubuntu-desktop! You don't want that, particularly on a dedicated server. It will drag in everything Xubuntu and you may as well have just installed Xubuntu in the first place.

```
sudo apt-get install xfce4
```

... is all you need. You only want the desktop environment, not Xubuntu ...

From a terminal:

```
startxfce4
```

... will get you to the desktop. You can also choose the xfce4 session from the Sessions menu at login screen, if you are running one.

If people are after the _desktop environment,_ please do not advise to install *buntu-desktop. Not the same at all. That command effectively installs the whole OS; apps, dependencies, the lot. Undesirable in many cases. ;)

---

### Post by guldberg72 on 2014-10-21
thanks for the anwser. i am not running any desktop enviroments at the moment because it is the server edition and i dont want to loose performance by running a desktop.
there is just sometimes it is a little easier when there is a desktop enviroment ;)

---

### Post by ibjsb4 on 2014-10-21
> If people are after the desktop environment, please do not advise to install *buntu-desktop. Not the same at all. That command effectively installs the whole OS; apps, dependencies, the lot. Undesirable in many cases.
I would consider something even lighter than xfce4, like lxde-core & xserver-xorg.

[http://packages.ubuntu.com/trusty/xfce4](http://packages.ubuntu.com/trusty/xfce4)

[http://packages.ubuntu.com/trusty/lxde-core](http://packages.ubuntu.com/trusty/lxde-core)

---

### Post by Impavidus on 2014-10-22
Keep in mind that if you install xfce4 on a server running an LTS release, the support period will be cut back from 5 years to just 3. After that, you'd get an unsupported GUI on a supported server, which gives trouble.

---

### Post by ibjsb4 on 2014-10-22
> **Impavidus said:**
> Keep in mind that if you install xfce4 on a server running an LTS release, the support period will be cut back from 5 years to just 3. After that, you'd get an unsupported GUI on a supported server, which gives trouble.
Good point.

Not all desktops have five years of support, Flashback (minimal) would give 5 years of support.
```
sudo apt-get install xserver-xorg gnome-terminal && sudo apt-get install --no-install recommends gnome-session-flashback nautilus
```
[http://packages.ubuntu.com/trusty/gnome-session-flashback](http://packages.ubuntu.com/trusty/gnome-session-flashback)
After you get whatever desktop installed you can check package support.
```
ubuntu-support-status --show-supported
```

---


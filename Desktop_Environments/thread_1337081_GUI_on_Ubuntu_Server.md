---
title: "GUI on Ubuntu Server"
date: 2009-11-25
forum: Desktop Environments
---

### Post by Aled Owen on 2009-11-25
I recieved my copy of Ubuntu 9.10 and Ubuntu Server 9.10 in the mail yesterday, I was wondering if I set Ubuntu Server up on an old computer I would be able to install a Graphical User Interface on it?

---

### Post by renzokuken on 2009-11-25
yes you can very easily, depending what DE you want e.g.

For GNOME
```
sudo apt-get install ubuntu-desktop
```

For KDE
```
sudo apt-get install kubuntu-desktop
```

For XFCE
```
sudo apt-get install xubuntu-desktop
```

....these will add all the respective packages (xorg/DE/login manager/etc/etc) for each desktop.

you could also do it manually by installing X and then picking something very lightweight such as fluxbox etc.

easiest way is probably to install xfce with the command above. its the most lightweight and most suitable for a server out of those 3 (particularly for an old computer). if you dont like it you can always do a... ```
sudo apt-get remove (x/k)ubuntu-desktop
```

...and try one of the others

EDIT: **section 1** on this page [http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html](http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html) might also help if you dont want stuff like open office

---

### Post by sakisds on 2009-11-25
Doing remove on (*)buntu-desktop won't work. (k/x)Ubuntu-desktop is a package pointing to others, no use removing it.

I suggest you use XFCE or LXDE because they are lightweight.

Installing LXDE:
```
sudo apt-get install [login] lxde
```
(At login put either kdm, or gdm. Both will work.)
Uninstalling LXDE is as simple as:
```
sudo apt-get remove lxde
```

Installation of XFCE is already been posted above.

---


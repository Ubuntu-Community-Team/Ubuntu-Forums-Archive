---
title: "Locking down Gnome"
date: 2006-04-11
forum: Desktop Environments
---

### Post by mbainrot on 2006-04-11
I have managed to setup a thin client and it works well (even though the server is a 750mhz box w/ 192mb ram & 3x 8.2gb hdds (2 running off soft raid))

How do i turn off (for limited users)
* Editing of Panels (like adding items, etc)
* Hiding menus (Such as hiding games, administrive settings)
* Disable various applications w/o uninstalling them (like gaim)
* Prevent use of the terminal

Operating System is Edubuntu (Ver 5.10)
Running Gnome 2.12.1 (Build Date 03/10/05)

I have done some background research (like i have found the user privledges page), And so far i cannot find anything...

Would someone be able to explain/post a link on how to do that stuff

Regards,
     Mbainrot

P.S. if my thread needs to be moved can the mover please PM so i can find it later on...

---

### Post by badrinarayan on 2006-04-11
See [http://www.gnome.org/learn/admin-guide/latest/ch10.html](http://www.gnome.org/learn/admin-guide/latest/ch10.html)
Also, you may want to try installing sabayon to see what it can do for you.

Ubuntu 6.06 "Dapper Drake" uses GNOME 2.14 and Pessulus (see [http://www.gnome.org/start/2.14/notes/en/rnadmins.html](http://www.gnome.org/start/2.14/notes/en/rnadmins.html))  is included in universe for this purpose.

---

### Post by aysiu on 2006-04-11
KDE has a kiosk mode:
[http://extragear.kde.org/apps/kiosktool/](http://extragear.kde.org/apps/kiosktool/)

---

### Post by mbainrot on 2006-04-12
thanks guys

edit: I have looked at the kiosktool, i need something that does not have to be compiled seeing i have had allot of problems with compiling stuff, and i cannot use synaptic at the moment because the server is'nt setup to go onto the main network

---

### Post by aysiu on 2006-04-12
I've had good luck *alien*ing in Fedora binaries.

Try this.

Download [this file](ftp://ftp.kde.org/pub/kde/stable/apps/KDE3.x/admin/kiosktool-1.0-1.fc3.i386.rpm) to your desktop.

Go to KMenu > System > Konsole (since it's a KDE kiosk tool, I'm going to assume you have KDE installed) and type ```
sudo apt-get update
sudo apt-get install alien
cd ~/Desktop
sudo alien -i kiosktool-1.0-1.fc3.i386.rpm
```

---


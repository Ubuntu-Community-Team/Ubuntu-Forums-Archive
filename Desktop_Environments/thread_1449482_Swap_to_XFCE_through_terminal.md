---
title: "Swap to XFCE through terminal?"
date: 2010-04-07
forum: Desktop Environments
---

### Post by BigCheese01 on 2010-04-07
I'm running a basic Ubuntu server, and I want to be able to connect to it via VNC graphically through xfce. Right now I've got Ubuntu installed with the Gnome Desktop and the VNC works fine. Xfce is installed as far as I can tell (I ran the aptitude command)

How can I keep the server from loading gnome at boot? Right now the VNC shows the gnome desktop I installed, but I can't get it to show the xfce. Tutorials I found want me to go to the options menu in the login screen, but because I'm using VNC there is none.

Any help would be great.

---

### Post by micio on 2010-04-08
1. you must log in grafically in local in order to set xfce as default desktop environment

2. also, you can force it by changing setting in /etc/gdm/somewhere here

3. I guess that you must set an "auto login" in grafic mode because as far as I remember vnc is connected to an already opened session. (I'm not so sure)

4. to log in through VNC you must set GDM to run as service at boot time (see update-rc.d --help to see how) (you don't need it if it is already running in automatic as service)

after all you may be able to log in remotely using VNC....

Just a suggestion.... 

since it is a server, and since an autologin is not the safety way to work, an ssh X11 fowarding would be better and safer... don't you?


Thanks

Micio

---


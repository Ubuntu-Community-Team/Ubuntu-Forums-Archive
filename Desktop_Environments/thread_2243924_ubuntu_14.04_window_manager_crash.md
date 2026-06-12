---
title: "ubuntu 14.04 window manager crash"
date: 2014-09-12
forum: Desktop Environments
---

### Post by Ntwobike on 2014-09-12
[COLOR=#333333][FONT=UbuntuRegular]Im currently using 14.04, recently installed Gnome desktop but now window manager is crashing every time. Cannot do anything [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular] with the keyboard[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular] after open a folder! ex: cannot copy a folder using keyboard cannot press crtl alt or shift key. Can anybody help me to correct this issue?[/FONT][/COLOR]

---

### Post by ibjsb4 on 2014-09-12
I am not so sure what your running.  At the login screen press Ctrl + Alt + F1 and login.  Then post the output of these commands:
```
echo $DESKTOP_SESSION
```
and
```
find /usr/share/xsessions -name "*.desktop" -exec basename "{}" .desktop ";"
```
Also what are your computer specs (cpu, ram, graphics)?

---

### Post by Ntwobike on 2014-09-13
Hi [COLOR=#000000]ibjsb4 here are the things you asked
[/COLOR][B]
echo $DESKTOP_SESSION[/B]
gnome

**find /usr/share/xsessions -name "*.desktop" -exec basename "{}" .desktop ";"**
cairo-dock
wmaker-common
gnome-classic
gnome

**System setting**
CPU : intel core i7 2670QM 2.2 GHz
Ram : 8GB DDR3
Graphics : Nvidia geforece GT540M 1GB

---

### Post by ibjsb4 on 2014-09-13
This could be a graphics issue.  From what I been reading the gt540m can be hard to set up.

[http://ubuntuforums.org/showthread.php?t=2113259](http://ubuntuforums.org/showthread.php?t=2113259)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Nvidia+geforce+GT540M&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Nvidia+geforce+GT540M&sa=Search&cof=FORID:9)

---

### Post by Ntwobike on 2014-09-13
actually it worked very well. then i installed gnome desktop after that this problem came :(

---

### Post by ibjsb4 on 2014-09-14
You say that you added gnome to your install so I am guessing that this is a custom build.

If you want the gnome environment, it may be better to go with UbuntuGnome.

[https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME](https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME)

---


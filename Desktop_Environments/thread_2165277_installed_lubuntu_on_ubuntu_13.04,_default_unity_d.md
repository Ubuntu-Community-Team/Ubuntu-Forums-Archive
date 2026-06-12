---
title: "installed lubuntu on ubuntu 13.04, default unity desktop only shows background."
date: 2013-08-04
forum: Desktop Environments
---

### Post by Ronaldus91 on 2013-08-04
I am pretty new to ubuntu and recently installed lubuntu desktop on my ubuntu 13.04 just using [COLOR=#666666][FONT=Consolas]*sudo apt-get install lubuntu-desktop *[/FONT][/COLOR]and now my default ubuntu desktop only shows the background and broken icons that I placed on my Lubuntu desktop.  I tried reinstalling unity but it did not work.  Also if I try to use sudo apt-get [anything] in unity there is no network access.

---

### Post by ibjsb4 on 2013-08-04
I would guess that you have a window manager conflict going on.  Try resetting compiz.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+compiz&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+compiz&sa=Search&cof=FORID:9)

---

### Post by Ronaldus91 on 2013-08-04
Thanks man. That worked, just entered "[COLOR=#000000][FONT=Tahoma]gconftool-2 --recursive-unset /apps/compiz" into command promt and it sorted it out.[/FONT][/COLOR]

---

### Post by ibjsb4 on 2013-08-04
Good show and welcome to the forums :D

---


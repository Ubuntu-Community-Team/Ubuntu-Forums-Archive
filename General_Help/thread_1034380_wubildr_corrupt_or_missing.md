---
title: "wubildr corrupt or missing"
date: 2009-01-08
forum: General Help
---

### Post by yagogak on 2009-01-08
Hi All, 

After a partition resize with Gparted, wubi won't boot anymore.

With bcdedit under windows i get the following lines : 

Secteur de démarrage en mode réel
---------------------------------
identificateur          {default}
device                  unknown
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu-Linux

"device is unknown", does anyone know how i can fix this ?

bcdedit /set {default} device partition=g did not work

thanks

---

### Post by Jammanuser on 2009-01-08
> **yagogak said:**
> Hi All, 

After a partition resize with Gparted, wubi won't boot anymore.

With bcdedit under windows i get the following lines : 

Secteur de démarrage en mode réel
---------------------------------
identificateur          {default}
device                  unknown
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu-Linux

"device is unknown", does anyone know how i can fix this ?

bcdedit /set {default} device partition=g did not work

thanks

I uploaded the 4 wubi files needed to boot. :) Hope it solves your problem! 

[http://www.mediafire.com/?cdyz3mjwgjd](http://www.mediafire.com/?cdyz3mjwgjd) (menu.lst)
[http://www.mediafire.com/?eytzmydnzjz](http://www.mediafire.com/?eytzmydnzjz) (wubildr)
[http://www.mediafire.com/?vmnn0mttjzi](http://www.mediafire.com/?vmnn0mttjzi) (wubildr.exe)
[http://www.mediafire.com/?jgdhwmjejmz](http://www.mediafire.com/?jgdhwmjejmz) (wubildr.mbr)

GL and let me know how it goes! 

-Jam man

:guitar:

---

### Post by yagogak on 2009-01-09
thanks, but my wubi files were ok.

I finally fix the problem, with :

bcdedit /set {default} device partition=g[COLOR="DarkRed"]**:**[/COLOR]

"[COLOR="DarkRed"]**:**[/COLOR]" missing ...

if you have the same problem, please be sure to use the good letter for your hard drive. Wubi stand on "g:" for me.

---


---
title: "[HELP!] Desktop Effects/Intel chip/Not working"
date: 2009-11-03
forum: Desktop Environments
---

### Post by Sourmiloko on 2009-11-03
[ubuntu 9.04 Jaunty]

Hi so I just installed Ubuntu and I love it, but the main reason I like it so much is the Compiz Destop effects. So at first I just went System>Preferences>Appearance and tryed to enable the desktop effects and it reported an error reading; "desktop effects could not be enabled." So I went online and found out that the following worked for most people;

(un-blacklisting the driver)
Code:
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```And

(rolling back the driver)
```
 deb http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
 deb-src http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
``````
sudo apt-get update
sudo apt-get install xserver-xorg-video-intel-2.4
```----------------------------------------------------------------------------

I also ran ./Compiz-check and this is what i got

```
 Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```____________________________________________
[FONT=Verdana][COLOR=Red]**Now after I try and run the desktop effects my computer shutters and all i get is the Desktop wallpaper and mouse... What do I need to do?**[/COLOR][/FONT]

---

### Post by Sourmiloko on 2009-11-03
Bump [Help please!]

---

### Post by Sourmiloko on 2009-11-03
My computer is a Compaq Presario SR1020NX 

And when I run compiz in the terminal it goes to the wallpaper and mouse again no menus and the keyboard stops interacting.... I REALLY WANT DESKTOP EFFECTS!!!!!   T_T

---

### Post by carolinason on 2009-11-03
this is weak but try upgrading to 9.10

---

### Post by Sourmiloko on 2009-11-03
I did that and had to reinstall 9.04 because it would log in with the cool new splash screen and after about five minuets would re-login and delete any changes i had made??? Also things just seemed very off, like green or purple lines as if corruption would appear in places, windows would go black... It was all around chaos so I switched back...

---

### Post by Sourmiloko on 2009-11-03
uggg -_______-  


(bump)

---


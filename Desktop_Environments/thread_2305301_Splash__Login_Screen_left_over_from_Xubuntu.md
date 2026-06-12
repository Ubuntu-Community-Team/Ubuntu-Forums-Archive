---
title: "Splash / Login Screen left over from Xubuntu"
date: 2015-12-04
forum: Desktop Environments
---

### Post by GaryTheCat on 2015-12-04
Hello

I recently installed Lubuntu on my laptop after a few minor but annoying issues with Xubuntu.

I've got Lubuntu set up as I want it but want to remove the Xubuntu login and splash screens.

I've tried ```
sudo apt-get remove xubuntu-desktop
sudo apt-get autoremove
sudo apt-get autoclean
```

but for some reason xubuntu is still installed and the splash / login screens are still there.

I've also tried the psychocats command but it's for a very old version and falls over after the first couple of packages.

Any help is most welcome.

Many thanks

---

### Post by SlidingHorn on 2015-12-04
You should be able to accomplish this by using update-alternatives:

```
sudo update-alternatives --config default.plymouth
```

---

### Post by GaryTheCat on 2015-12-04
Thank you!

It's changed the splash screen at boot and shut down but the xubuntu / xfce login screen is still there.

Happy with being at the halfway point but would like to sort the login screen if that's possible?

---

### Post by SlidingHorn on 2015-12-04
If I remember correctly, you should be able to change this by editing your **/etc/lightdm/lightdm-gtk-greeter-ubuntu.conf** file and change the background line to the following:

```
background=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png
```

---

### Post by GaryTheCat on 2015-12-04
Thanks again :-)

I tried to edit **/etc/lightdm/lightdm-gtk-greeter-ubuntu.conf** with gksu leafpad but the file was empty. There is an **/etc/lxdm/default.conf** file but the background is set to

> ## background of the greeter
bg=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png

My poor brain - it hurts.  It's one of my problems with anything computer related - I can make it work but I can't make it look pretty!

---

### Post by SlidingHorn on 2015-12-04
> **GaryTheCat said:**
> Thanks again :-)

I tried to edit **/etc/lightdm/lightdm-gtk-greeter-ubuntu.conf** with gksu leafpad but the file was empty. There is an **/etc/lxdm/default.conf** file but the background is set to



My poor brain - it hurts.  It's one of my problems with anything computer related - I can make it work but I can't make it look pretty!

What is listed in the /etc/lightdm/ directory?

```
ls /etc/lightdm
```

---

### Post by GaryTheCat on 2015-12-06
Sorry for the delay - pesky kids!

> lightdm.conf.d            lightdm-gtk-greeter.conf.dlightdm-gtk-greeter.conf  users.conf




---

### Post by SlidingHorn on 2015-12-06
You should be able to set the background by editing /etc/lightdm/lightdm-gtk-greeter.conf

```
[greeter]
background=/path/to/image.png
```

According to what I'm reading (Arch Wiki), it's recommended to put your image in /usr/share/pixmaps to allow LightDM access to the file.

---

### Post by Bucky Ball on 2015-12-06
I use lightdm and /etc/lightdm/lightdm-gtk-greeter.conf doesn't exist on my machine. Maybe its an Arch thing. Curious to know if that file exists for the OP. :-k

---

### Post by vasa1 on 2015-12-06
On my machine, standard Lubuntu 14.04.3 LTS, fully updated, I have:```
09:24 AM /etc/lightdm $ ls -AlR
.:
total 12
drwxr-xr-x 2 root root 4096 Jul 23  2014 lightdm.conf.d
lrwxrwxrwx 1 root root   55 Nov 14  2014 lightdm-gtk-greeter.conf -> /etc/alternatives/lightdm-gtk-greeter-config-derivative
-rw-r--r-- 1 root root 1317 Mar 13  2014 lightdm-gtk-greeter-ubuntu.conf
-rw-r--r-- 1 root root  452 Oct 31  2014 users.conf

./lightdm.conf.d:
total 4
-rw-r--r-- 1 root root 36 Dec 14  2013 20-lubuntu.conf
09:24 AM /etc/lightdm $ 

```and the contents of *lightdm-gtk-greeter.conf -> /etc/alternatives/lightdm-gtk-greeter-config-derivative* are below:```
#
# logo = Logo file to use, either an image absolute path, or a path relative to the greeter data directory
# background = Background file to use, either an image path or a color (e.g. #772953)
# theme-name = GTK+ theme to use
# icon-theme-name = Icon theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (none, slight, medium, or full)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
# show-language-selector (true or false)
# show-indicators = semi-colon ";" separated list of allowed indicator modules (e.g. libsoundmenu.so)
# show-clock (true or false)
# clock-format = strftime-format string, e.g. %H:%M
# keyboard = command to launch on-screen keyboard
#
[greeter]
logo=/usr/share/icons/lubuntu/places/64/start-here.svg
background=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png
theme-name=Lubuntu-default
icon-theme-name=lubuntu
font-name=Ubuntu
xft-antialias=true
#xft-dpi=
xft-hintstyle=full
xft-rgba=rgb
show-language-selector=true
#show-clock=
#clock-format=
#keyboard=
```I'm adding this thread's link to my collection of "things that happen when multiple DEs are installed". Many wikis and tech articles don't deal with issues such as OP is facing.

---

### Post by GaryTheCat on 2015-12-07
Ah the OP sure is facing them lol!

ok then:

> 
gary@gary-Inspiron-1720:/etc/lightdm$ ls -AlR
.:
total 16
drwxr-xr-x 2 root root 4096 Dec 13  2014 lightdm.conf.d
-rw-r--r-- 1 root root 2757 Aug  7 02:24 lightdm-gtk-greeter.conf
drwxr-xr-x 2 root root 4096 Dec  4 22:41 lightdm-gtk-greeter.conf.d
-rw-r--r-- 1 root root  452 Oct 30  2014 users.conf


./lightdm.conf.d:
total 4
-rw-r--r-- 1 root root 36 Jul 15  2014 10-xubuntu.conf


./lightdm-gtk-greeter.conf.d:
total 12
-rw-r--r-- 1 root root  340 Jun 26 09:17 01_ubuntu.conf
-rw-r--r-- 1 root root 2920 Oct 13 11:23 30_lubuntu.conf
-rw-r--r-- 1 root root 2224 Sep  6 23:02 30_xubuntu.conf




oooh I see a problem - but I'm not sure what the consequences of fixing it by deleting the #'s will be:

> [greeter]#background=
#user-background=
#theme-name=
#icon-theme-name=
#font-name=
#xft-antialias=
#xft-dpi=
#xft-hintstyle=
#xft-rgba=
#indicators=
#clock-format=
#keyboard=
#reader=
#position=
#screensaver-timeout=




---

### Post by Dennis N on 2015-12-07
> **GaryTheCat said:**
> Ah the OP sure is facing them lol! ok then: oooh I see a problem - but I'm not sure what the consequences of fixing it by deleting the #'s will be:

The section beginning [greeter] is where the system looks to define appearance/feature settings in the lightdm greeter.

The lines beginning with # are skipped when parsed by the system. If you want to supply a value to any of these, delete the # and  type the value after = and it will be used (but it could be overridden somewhere else in some cases). Looks like yours are somehow undefined, which is not normal after a new install. At least some are usually defined (as in vasa1's display).

---

### Post by GaryTheCat on 2015-12-09
what I can't quite figure out is which:

1.  Which config file is setting the splash / login screen as there seems to be more than one; and
2.  What file in the system is telling lubuntu to use that particular config file?

---


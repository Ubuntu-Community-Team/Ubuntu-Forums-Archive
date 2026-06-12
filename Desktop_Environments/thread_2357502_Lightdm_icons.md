---
title: "Lightdm icons"
date: 2017-04-03
forum: Desktop Environments
---

### Post by paralis on 2017-04-03
On 16.10, I have noticed lightdm doesn't use the icon theme used on the desktop (as far as I can tell it uses the ubuntu-mono-dark theme).
Is there any way to use the same theme on both the desktop and lightdm?

Thank you

Eric

---

### Post by Dennis N on 2017-04-03
You can try and edit **/etc/lightdm/lightdm-gtk-greeter.conf ** (below) or appropriate file could be **lightdm-gtk-greeter-ubuntu.conf** in some desktop environments.
Find the section [greeter] in that file (see below)

```
[dmn@Kayleigh ~]$ cat /etc/lightdm/lightdm-gtk-greeter.conf 
[greeter]
background=/lib/plymouth/themes/xubuntu-logo/wallpaper.png
theme-name=Greybird
icon-theme-name=elementary-xfce-dark
font-name=Droid Sans 10
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-indicators=power;~session;~language;~a11y;~power;
show-clock=true
clock-format=%I:%M %p 
keyboard=onboard

```

Be sure to remove the comment character (#) from any line you want to be active.

Note: Some distros and desktop environments have a GUI configuration utility for this. Check for it first.

System used for above: Xubuntu 14.04

---

### Post by paralis on 2017-04-03
Thank you for your quick answer.
I tried that to use the Papirus icon theme I use already on the desktop:

```
icon-theme-name=/home/myuser/.icons/Papirus
``` But, despite a noticably longer boot time, icons are still from the ubuntu-mono-dark theme, so no change. It does not work.

Eric

---

### Post by Perfect Storm on 2017-04-03
You properly need the icon themes installed at /usr/share/icons (globally) to get it to work. I don't think it will work if you sset it locally.

---


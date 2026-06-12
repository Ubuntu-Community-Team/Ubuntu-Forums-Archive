---
title: "Tiny icons after fresh install"
date: 2014-09-13
forum: Desktop Environments
---

### Post by SOME1 on 2014-09-13
Hello. 
I installed ubuntugnome 14.04.1 (new install not upgrade).
I am using a pc with nvidia ion. 
after install icons and fonts is extremely small. 
changing screen resolution didn't help.
I tried to install nvidia property driver but there is no change.
I add to xorg.conf Option "DPI" "96 x 96"
now the fonts are ok but the icons is very small, mainly in the menus. 
I upload a scrrenshot to [here]("http://s14.postimg.org/3n6hrpm0h/Untitled.jpg")

thanks for your help

---

### Post by redrumrogue on 2014-09-13
I had a similar problem after installing Ubuntu Gnome 14.04 and found that I had to set the desktop interface scaling to a value of 1.  To do this type the following in terminal ... (as current user, not root)

** gsettings set org.gnome.desktop.interface scaling-factor 1**

You will need to reboot as well for the change to take full effect.

You can set this property through dconf-editor GUI as well.

Hope it helps!

---


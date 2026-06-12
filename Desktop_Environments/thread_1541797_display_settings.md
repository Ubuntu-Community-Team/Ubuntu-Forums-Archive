---
title: "display settings"
date: 2010-07-29
forum: Desktop Environments
---

### Post by sh3rif on 2010-07-29
Hi
I have a netbook with ubuntu 9.10 and i have to change the display settings very often (external display @ home and a projector in school ) is there a way to save them and then load them with a script when needed ?

thanks :)

---

### Post by Kakers on 2010-07-29
Yes, the two parts you want to look into is your xorg.conf (/etc/X11/xorg.cfg) and xrandr

[http://www.freebsd.org/doc/handbook/x-config.html](http://www.freebsd.org/doc/handbook/x-config.html)
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

### Post by sh3rif on 2010-07-30
thx i have found a solution 

[http://ubuntuforums.org/showthread.php?p=4211618](http://ubuntuforums.org/showthread.php?p=4211618)


home scipt 

xrandr --output LVDS1  --off  #internal monitor off

xrandr --output VGA1 --auto    #vga on

xrandr --output VGA1 --mode "1152x864" 


laptop script

xrandr --output VGA1 --off #vga off

xrandr --output LVDS1 --auto #internal monitor on

xrandr --output LVDS1 --mode "1024x600"

---


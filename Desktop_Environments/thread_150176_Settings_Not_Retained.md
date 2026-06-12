---
title: "Settings Not Retained"
date: 2006-03-25
forum: Desktop Environments
---

### Post by Geffers on 2006-03-25
This is driving me mad ](*,) 

I keep resetting (Or think I am) the screen resolution using system settings from the K menu.

I click apply then accept but each time I restart I am back to the original again.

I've tried this running System Settings as root and as me but each time it is back to normal.

Am I missing a Save option somewhere.

Geffers

---

### Post by ajgreeny on 2006-03-25
You need to set the default resolution by doing a 
"sudo dpkg -reconfigure xserver-xorg"
Set you required res and then restart x (by doing a alt+ctrl+backspace, I think)

OR

Simply edit your /etc/X11/xorg.conf as root and manually change the resolution and colour depth to what you want, as well as the hor and vert res rates of your monitor.
Good luck!

---

### Post by aysiu on 2006-03-25
Press Alt-F2 and type ```
kcontrol
``` and go to Peripherals > Display

Check the box that says "Apply settings at KDE startup."

---

### Post by Geffers on 2006-03-25
[QUOTE=aysiu]Press Alt-F2 and type ```
kcontrol
``` and go to Peripherals > Display

Check the box that says "Apply settings at KDE startup."[/QUOTE]

Apply at Start Up, damn, I missed that one, working now :) 

Thanks

Geffers

---


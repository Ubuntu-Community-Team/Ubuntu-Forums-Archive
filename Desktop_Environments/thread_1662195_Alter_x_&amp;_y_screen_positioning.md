---
title: "Alter x &amp; y screen positioning"
date: 2011-01-07
forum: Desktop Environments
---

### Post by Raifj on 2011-01-07
Hi New to the forum as a poster, but have been poking around for a couple of years.

I have an Ubuntu 10.4 install, which i use as a media server @ hom and is linked directley to my 37" 1080p LCD.

I struggled with getting my box to register my TV resolution settings but evential managed to configure Ubuntu with the following:

```
xrandr --newmode <Modeline>
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr --output VGA1 --mode 1920x1080_60.00
$gksudo gedit /etc/gdm/Init/Default
```Which has given me the desired resolution settings.

The issue i have is that my desktop extends 10 mm of the top edge of the screen, this means that if any windows are maximised the window controls are hidden.

Any direction for a fix would be much appreciated 

Cheers

---

### Post by Krytarik on 2011-01-08
> **Raifj said:**
> Hi New to the forum as a poster, but have been poking around for a couple of years.So as I! Welcome then! :-)
> **Raifj said:**
> ```

[COLOR=Red]xrandr --newmode <Modeline>    # this line can be removed, doesn't matter anyway
[/COLOR]xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr --output VGA1 --mode 1920x1080_60.00
$gksudo gedit /etc/gdm/Init/Default
```
> **Raifj said:**
> The issue i have is that my desktop extends 10 mm of the top edge of the screen, this means that if any windows are maximised the window controls are hidden.
I had the same issue with a LCD-TV recently, fixed it through the input options of the screen.

---


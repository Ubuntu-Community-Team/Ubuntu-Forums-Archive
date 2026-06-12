---
title: "gnome problem with &quot;separate x screen&quot; setup."
date: 2009-03-01
forum: Desktop Environments
---

### Post by cheise on 2009-03-01
Hi,

i'm currently running a clean installation of Ubuntu 8.10 on my laptop with an LCD-TV connected via HDMI. I installed nvidia linux drivers 180.35 and used nvidia-settings to configure 2 "separated x screens":

screen0 (laptop) runs at 1280x800
screen1 (lcd) runs at 1920x1080

So far, everything is working as expected... but:

On the LCD screen, gnome only displays itself (wallpaper, windows...) at a size of 1280x800 which is the resolution of the main screen. The rest of the screen is just a black border, where I can move my mousepointer on.

I tried xinerama and TwinView, which works just fine (over the full 1920x1080), but i prefer the separated x screen setup.

I tried xubuntu8.10 with the exact configuration and it seems that xfce doesn't have this problem, it works as expected.

My question now is, how can I force Gnome to display itself over the full scale of 1920x1080 on screen1.

greetings from germany
cheise :D




(I do not include my xorg.conf because I'm sure it's not an xserver problem)

---


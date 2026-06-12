---
title: "Duplicate desktop icons with a Xrandr-configured extended desktop"
date: 2013-06-24
forum: Desktop Environments
---

### Post by Krallice on 2013-06-24
Hi folks! Since I've been enjoying lubuntu 13.04 very much on my netbook I' ve taken the step to also install it on my desktop. 
I' m using two monitors and I've almost managed to get it to extend properly with xrandr. To make it work each time I reboot I changed the the autostart file
located here:

/etc/xdg/lxsession/Lubuntu/autostart

This is what I added:

```
@xrandr --output DIN --off --output DVI-1 --mode 1440x900 --pos 1024x0 --rotate normal --output DVI-0 --mode 1024x768 --pos 0x0 --rotate normal
@xrandr --output LVDS --off

```

Basically, everything is working smoothly but there is one thing that I can't seem to figure out, I can move windows between my two monitors like a normal extended desktop, Desktop icons however are cloned. If i create a new folder in either desktop, it recreates it in the other, same goes for deleting. Am I missing something in my code that can prevent it, or is there another setting somewhere that I overlooked? 

I have disabled Lxrandr from startup so it doesn't interfere.

With regards,

Ryan

---


---
title: "gutsy dual monitor setup with external nvidia fx 5200 card"
date: 2007-11-03
forum: Desktop Environments
---

### Post by gnuyoga on 2007-11-03
My configuration:
 Core 2 Duo + Intel 965 Motherboard + External Nvidia (fx5200 geforce) card 

I was very much exited when i got to know that gutsy was released. Invoked my torrent client and got gutsy downloaded in 1 day .... wanted to change my f..k..g fedora .... ;) ....  

booted the live cd to know that kernel hangs when its initializing devices ..... did a lot of googling with no result ... for almost 5 hours ... finally i got a old post which talks about blacklisting a module..... 

slowly things were in control.... 

1. Removed my external nvidia card ... 
2. installed gutsy (ubuntu 7.10) using internal intel_apg display support
3. apt-get install nvidia-glx 
4. vi /etc/modprobe.d/blacklist 
     blacklist intel_agp
5. remove splash from /etc/grub.conf (or from /boot/grub/menu.lst)
6. inserted my external nvidia geforece fx5200 card 
7. ahhooooooooooooo ... my display is working 
8. now fun starts .... dual monitor setup and compiz (desktop effect)
9. /etc/X11/xorg.conf  Device section add  
Option "TwinView" "On" 
10. voila .... desktop is extended to two monitor 
11. sudo apt-get install xgl
12. restart gdm ....... now i have two 17'' samsung monitor running at high resolution 



- gy

---

### Post by Miso Horni on 2007-11-08
Glad to see gnuyoga got his displays working. Unfortunately these directions don't work for my nvidia fx 5200

1. Is nvidia-glx the correct driver for the fx 5200? Ubuntu reports it should be nvidia-glx-new
2. Is there a package called xgl? No. The package is xserver-xgl

btw: It looks like the xgl layer is scaling videos really poorly on the fx 5200. The image is pixelated and there's what looks like a diagonal line running from top left to bottom right because the two sides aren't joined in sync. The frame rate is abysmal.

Disabling the xgl layer fixes this but you lose all the desktop effects.

This can be done by

1 .sudo apt-get remove xserver-xgl
2. restart

For now I'd rather have a 2-D desktop with tv-out working again.

Does anyone else have tv-out or dual-monitor working on Gutsy with an nvidia fx 520

---


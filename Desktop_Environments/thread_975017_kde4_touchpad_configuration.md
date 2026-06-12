---
title: "kde4 touchpad configuration"
date: 2008-11-08
forum: Desktop Environments
---

### Post by systemshq on 2008-11-08
I've just installed kde4 on top of my ubuntu intrepid installation but I can't find any utility to configure my touchpad in kde4?

---

### Post by pads on 2009-05-08
hi. 

i have the same problem, there is no config application for touchpad. 
it's extremely annoying when you use usb mouse and that touchpad keeps on interrupting you. In gnome there is simple utility to switch off the touchpad... how can I do it in KDE4??? i'm using kubuntu 9.04...

please help. 

ps. as i know... any change to xorg.conf - doesn't make it any better.

---

### Post by pads on 2009-05-08
hey. for all having similar problem with kde4 + touchpad on their laptops, here is workaround that worked for me... 

i just typed in: 
> sudo modprobe -r -v psmouse

:D the touchpad is swithed off... reboot swith it on again. 
so if anyone can help with that... to make it permanent - or to be able to disable or enable it as it goes, please help. I provided workaround :) 

ps. im using dell xps m1530. cheers.

edit! (full instructions) 
- to make the changes permanent: 
add the following line to your /etc/modules - file, just type in command

>sudo kate /etc/modules 

add the line: psmouse proto=exps 

then in case it's working (i mean touchpad :P) type in again: 
> sudo modprobe -r -v psmouse

after restart, it should be switched off for good :D 

i hope, i helped you :) 
and i hope KDE guys will create good tool for managing touchpad. 

for begginer gnome guys - DONT'T USE THESE COMMANDS - you have nice tool in your system panel that works... heh.

---


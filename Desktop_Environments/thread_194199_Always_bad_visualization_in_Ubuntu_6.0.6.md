---
title: "Always bad visualization in Ubuntu 6.0.6"
date: 2006-06-11
forum: Desktop Environments
---

### Post by carontis on 2006-06-11
Hellò. Situation after updating stills here bad. Every time Ubuntu loads the login, the splash screeen is doubled and icons I mounted in the tray bar disappeared. When I oper the foruma page and log in it, Ubuntu shows me doubled frames, everything is out of its place; the same happens when I launch Firefox and open my web site page... I think a bug still in the somewhere, but I can't undrstand where. Does anyone have idea of what/how to do for fixing it? I use Ubuntu with Gnome, on an AMD 1700+ and a vga S3 Savage 32 Mb AGP. 
Thanks

---

### Post by jeremyk on 2006-06-11
I don't know your graphics card. But until you fix with all option, you could use vesa driver. This would probably solve your problem, but this will also slow your system. 

Do:

cd /etc/x11
sudo cp xorg.conf xorg.conf.bak
sudo gedit xorg.conf
and change the driver to vesa.

Then do: trl+Alt+backspace to restart X.

Before that check:
System->preferences->screen resolution

---

### Post by carontis on 2006-06-11
Well, thank for giving me help, but I don't think is done exactly to the driver itself, but to something happened after the updating. In effect when I installed Ubuntu 6.0.4 Beta from the cd, everything was working fine. All this happened after I started to update the OS. With the first updating it eated the down icon dvd I made (Drive Mount) leaving there only the one for fd0. After an update this is very bad' 'cause it's supposed updates should fix problems and not making them...
Do you really think th way you described me can be a good way? I wouldn't create more troubles tha what I have now...
I'll try
Thanks

After Tried: nothing happens and the situation still the same; doubled frames in Firefox and the down tray icon (dvd) is not appeared... So I think it must be some kind o bug in my pc configuration...
 or in some downloaded part of the update, that was automatic... No other to try?
Thanks

---


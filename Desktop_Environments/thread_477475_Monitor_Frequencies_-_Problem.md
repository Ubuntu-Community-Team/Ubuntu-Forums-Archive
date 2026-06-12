---
title: "Monitor Frequencies - Problem"
date: 2007-06-18
forum: Desktop Environments
---

### Post by pinguino99 on 2007-06-18
I posted this also in laptop forum ...sorry.



Hello everyone, 
I am new to this forum so please be kind with me !
I am moving from fedora to ubuntu, i find it easier to use.
My problem:
I installed feisty on my pc, videocard geforce 5600xt ultra with nvidia-glx-new drivers.
Monitor is crt 17", acer ac711.
In gnome, screen resolution, i can correctly choose resolutions 1280x1024 , 1024x768 and 800x600.
But i cannot chooese exact frequency. For example, monitor supports 1024x768 at 85 hz but in the gnome screen resolution application i only can choose 50-51-52-58-59 hz (not exactly sure about numers but it is more or less exact).
Same thing (with different frequencies) for all resoluions, lower than the good ones.
This problem makes almost impossible to play opengl games : screen flickers, or black screen etc.
I tried almost everything in xorg.conf : 
specified correct horizontal and vert refresh rates
enabled/disabled useedi 
enabled/disabled many parameters (composite, addrgbvisuals etc)
reconfigured xorg with dpkg-reconfigure -phigh xserver-xorg or dpkg-reconfigure -phigh xserver-xorg
and even gnome gconf.
Nothing solved the problem !
Ah, of course i also have problems using compiz/bery, i suppose because wrong monitor frequency.

I accept any suggestion !!
Ah ... in windows everything is ok, so hardware works.
Motherboard is asus a7v8x-x

Thanks to everyone and greetings from Italia !

---


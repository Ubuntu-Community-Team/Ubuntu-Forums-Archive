---
title: "help with graphics"
date: 2005-11-12
forum: Desktop Environments
---

### Post by davgard on 2005-11-12
how do I re-configure display graphics. what command is used for Kubuntu?:confused:

---

### Post by ace2005 on 2005-11-12
Pick Failsafe when starting the computer and run this:

dpkg-reconfigure xserver-xorg

---

### Post by 23meg on 2005-11-12
```
sudo dpkg-reconfigure xserver-xorg
``` is most likely what you're looking for, but you have to be more specific; what exactly are you trying to configure?

---

### Post by az on 2005-11-12
[QUOTE=ace2005]Pick Failsafe when starting the computer and run this:

dpkg-reconfigure xserver-xorg[/QUOTE]


It is called "Recovery Mode" in the grub boot menu...  Hit escape when you boot if you are not shown the grub menu.

---

### Post by davgard on 2005-11-12
of course the monitor display is wrong, i think. the screen bows in towards the center on the left an right sides. I have  Trident-Blade 3d vid card and a 17" hp ultra vga 1280 monitor. I prefer 1024x768.

---

### Post by tseliot on 2005-11-12
[QUOTE=davgard]of course the monitor display is wrong, i think. the screen bows in towards the center on the left an right sides. I have  Trident-Blade 3d vid card and a 17" hp ultra vga 1280 monitor. I prefer 1024x768.[/QUOTE]

If I have understood your problem perhaps you should use the manual (physical) commands available on your Monitor. There are some buttons you have to use in order to move the area which is displayed. If you don't know how to do it you should read the manual of your monitor

---


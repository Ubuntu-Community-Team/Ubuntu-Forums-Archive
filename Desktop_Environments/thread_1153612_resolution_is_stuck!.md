---
title: "resolution is stuck!"
date: 2009-05-08
forum: Desktop Environments
---

### Post by bridgetgibbons on 2009-05-08
My computer is just trying to make me look like an idiot. I'm very new to Linux and I'm trying to learn but its very frustrating when my computer is zoomed in too much. This happened when I accidentally changed the resolution from 800x600 to 640x480. I need a much larger resolution but I'm not even going to try that yet. [COLOR=Red]I can get to the resolution page but because the screen is zoomed in so much the apply button is off screen[/COLOR]. I can select the new resolution but I can't apply it no matter how much I try to scroll and resize and whatnot. Hopefully this is an easy fix. thanks

---

### Post by KittyChow on 2009-05-09
try
```
sudo gedit/etc/X11/xorg.conf
  
```
there should be a section like 
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "[COLOR=Red]1920x1200[/COLOR] +0+0"
    SubSection     "Display"
        Depth       24/etc/X11/xorg.conf
    EndSubSection
```
try replacing the red number with a suitable resolution
im not realy new at linux per se but i dont know too much either 
hope it helped!

---

### Post by JK3mp on 2009-05-09
The above solution will help. But you probably need the appropriate gfx card drivers installed. You can get that through hardware > propreitary drivers i believe.

---


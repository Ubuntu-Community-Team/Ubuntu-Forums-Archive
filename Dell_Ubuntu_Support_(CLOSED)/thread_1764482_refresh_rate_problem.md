---
title: "refresh rate problem"
date: 2011-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tekin on 2011-05-21
Hello I have a Casper (domestic firm) computer. I have installed Ubuntu for a week. But my eyes is tired for my monitors refresh rate. it was 50 hz and I couldnt change it. then I changed 1024x768 then it raised to 60 hz but it s not available yet. I tried the xorg.conf but script is like this 

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

and there is no monitor data in it. Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

and in it there is no monitor data and I cant change it. 
question 2. My laptops monitor data I cant take from my firm. then are there any method for learning monitor spesifications?

Thanks

---


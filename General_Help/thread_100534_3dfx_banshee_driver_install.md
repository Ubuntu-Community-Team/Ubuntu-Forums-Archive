---
title: "3dfx banshee driver install"
date: 2005-12-07
forum: General Help
---

### Post by oldmanstan on 2005-12-07
Which libraries would i need to run a 3dfx banshee graphics card, not terribly concerned with 3d accel., only need 2d functionality.

Also, what is the name of the driver to use in the xorg.conf file? I used apt to get the glide3 library which is, i think, the one i need but then i couldn't figure out the name of the driver to use.

thanks

---

### Post by Appolusionist on 2005-12-08
[quote=oldmanstan]Which libraries would i need to run a 3dfx banshee graphics card, not terribly concerned with 3d accel., only need 2d functionality.
 
Also, what is the name of the driver to use in the xorg.conf file? I used apt to get the glide3 library which is, i think, the one i need but then i couldn't figure out the name of the driver to use.
 
thanks[/quote]
 
I think I might have a couple of those cards sitting in my closet. I google'd it and found the following. Hope it helps. 
 
> Section "Module" 
    Load        "dbe" 
    SubSection  "extmod" 
      Option    "omit xfree86-dga" 
    EndSubSection 
    Load        "type1" 
    Load        "freetype" 
    Load        "glx" 
    Load        "dri" 
EndSection 

Section "dri" 
  Mode 0666 
EndSection 

... 

Section "Device" 
    Identifier  "Card" 
    Driver      "tdfx" 
    Option     "EnablePageFlip" "True" 
EndSection 

Section "Screen" 
    Identifier  "Screen 1" 
    Device      "Monitor" 
    Monitor     "Monitor" 
    DefaultDepth 16 
    Subsection "Display" 
        Depth       16 
        Modes       "1024x768" "800x600" "640x480" 
        ViewPort    0 0 
    EndSubsection 
EndSection

---

### Post by oldmanstan on 2005-12-08
Thanks! I actually google'd it myself after posting and probably found the same page. I love getting to use old hardware again under linux

---


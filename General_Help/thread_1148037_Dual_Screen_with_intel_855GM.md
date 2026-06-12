---
title: "Dual Screen with intel 855GM"
date: 2009-05-04
forum: General Help
---

### Post by ElBucho on 2009-05-04
Hi all,

I'm running ubuntu 8.10 on my old Toshiba Tecra A2 equiped with an intel 855GM graph card. I want to setup a dual screen with my Samsung syncmaster 15". I tried to change my xorg.conf, even though I didn't quite understand what I was doing, just trying what others did...  Anyway, i cannot make it work. Using the screen resolution I can have a virtual second screen, meaning I can move the cursor of my mouse away from my current desktop, but nothing shows up on the other screen. So it looks like to me, that the computer can handle a second screen, but no signal goes out of the VGA plug to the screen.

Could anyone give me a hand on this ?

thanks

Here is my default xorg.conf

############
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    2048 768
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection
############

---


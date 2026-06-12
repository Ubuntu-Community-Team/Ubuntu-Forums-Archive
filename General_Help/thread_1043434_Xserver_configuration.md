---
title: "Xserver configuration"
date: 2009-01-18
forum: General Help
---

### Post by geezerone on 2009-01-18
Hi

After replacing a 9800Pro with a 4830 card the 3D effects (compiz) has gone as has the restricted driver. I have tried dpkg-reconfigure xserver-xorg but only keyboard settings are detected.

Here is a sample of my xorg.conf file:

```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
```I really only want to rely on tested ATI drivers from Ubuntu rather than cutting-edge ATI drivers.

---

### Post by gettinoriginal on 2009-01-18
I can't tell you much about ATI, I primarily use nVidia cards, so I cannot tell you if this will work. As far as installation goes, I would go about it in the following way: First, disable the proprietary nVidia driver via System>Administration>Hardware Drivers. Then shut down and install the new card.  Then boot into Ubuntu. If it boots fine, then just go ahead to enable the new restricted driver for the ATI card; if not, then boot into recovery mode and choose the 'xfix' option, and that should do it. Then resume normal boot.

---

### Post by geezerone on 2009-01-22
Done that but when I look in Restricted Driver there is none specified. I can use in 2D mode but think the latest ATI cards isn't yet supported by Ubuntu.

Anyone actually got an ATI 4800 card and if so have you managed to get proprietary drivers working successfully with it?

---

### Post by gettinoriginal on 2009-01-22
I have researched this, and find no solution with default drivers.  You may have to get it from ATI.

---

### Post by geezerone on 2009-01-23
Thanks. I was trying to download the other night but was taking ages so left until today.


I downloaded the ATI 8.561 driver today and rebooted into recovery mode.

Changed to my download directory then '[COLOR=Blue]*sudo sh ./ati-driver-installer-8-12-x86.x86_64.run*[/COLOR]'

Selected to install proprietary driver, accepted agreement, used recommended configuration option and hey didn't it work! ;)

Now running latest ATI driver for my lovely 4830 :D

---


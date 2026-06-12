---
title: "[SOLVED] Do I need ATI fglrx drivers for my Radeon 9200?"
date: 2007-08-08
forum: Gaming &amp; Leisure
---

### Post by mysticmatrix on 2007-08-08
I have a ATI radeon 9200 card and need to know that how do I install fglrx drivers for playing games. The ubuntu wiki([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) states that Open Source radeon drivers are enough for me and they state that  ATI drivers don't support cards below 9500.
I am geeting preety poor performance in glxgears(about 800 FPs).

I just need to play games at decent speed.

---

### Post by dougfractal on 2007-08-08
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

backup
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
```

so ```
sudo gedit /etc/X11/xorg.conf
```
change the Section "Device" 
but also mod your xorg.conf
```
Section "Device"
Identifier "Radeon"
Boardname "ATI Technologies, Inc. Radeon 9200"
VendorName "ATI Technologies"
Driver "radeon"
BusID "PCI:1:0:0"
Option "RenderAccel" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "True"
Option "UseInternalAGPGART" "no"
Option "backingstore" "true"
Option "AllowGLXWithComposite" "true"
EndSection
```

make sure device is "screen"  is correct.
> Section "Screen"
        Device          "radeon"

---


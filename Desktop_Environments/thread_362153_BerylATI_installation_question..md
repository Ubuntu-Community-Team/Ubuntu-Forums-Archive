---
title: "Beryl/ATI installation question."
date: 2007-02-15
forum: Desktop Environments
---

### Post by ljpm on 2007-02-15
Hi all,

I have attempted to install beryl on an Edgy system (upgraded from Dapper) with an ATI xpress 200 on board video card. I had previously installed the ATI drivers.

The instructions I followed are from 

[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

It states on this page that > ensure you have the open source radeon drivers installed.

Are these the drivers supplied by ATI? 

My first problem was 
```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
```



I corrected this problem by creating an xlg desktop file (xgl.desktop) using the instructions found here;

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

Now I get the following error;

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display localhost:1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
```

Any suggestions???

---

### Post by shareMenaPeace on 2007-02-15
Hmm are you sure you disabled the composite in xorg.conf?
[http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html](http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html)


```
Section "Extensions"
Option "Composite" "0"
EndSection
```

---


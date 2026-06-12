---
title: "Beryl:  Checking for XComposite extension               : failed"
date: 2007-02-09
forum: Desktop Environments
---

### Post by ljpm on 2007-02-09
Hi All,

I just installed Beryl on Edgy (ati xpress 200 video with ati drivers) using:

[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

The installation seemed to work fine.

When I started beryl-manger it started up but I had the following error in the terminal.
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

Anyone know that this means and how to fix.

---

### Post by shareMenaPeace on 2007-02-09
Did you changed the default session when you logged in?

---

### Post by ljpm on 2007-02-09
Not initially. I didn't have the option for xgl.

I found this guide:
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

and created /usr/bin/startxgl which gave me the option of xgl.

I now received this error:

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


This seems to be a common error and I am currently doing some (lots) of reading trying to solve the problem. If any one can offer assistants it will be appreciated.

---

### Post by devillighter on 2007-02-10
I am having the exact same problem.

When I enable composite in xorg.conf, I get the "XFree86-DRI" missing error

When I disable composite in xorg.xonf, I get the "No composite extension error"

fglrxinfo shows that my driver is correctly installed

---

### Post by ultima_nota on 2007-03-07
I have the same problem with kubuntu and radeon 9800 pro...
can anyone help us?

---

### Post by bvidinli on 2007-03-07
I am having the exact same problem.

When I enable composite in xorg.conf, I get the "XFree86-DRI" missing error

When I disable composite in xorg.xonf, I get the "No composite extension error"

i use ati radeon mobility x1600

i followed [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)


bvidinli@bvidinli-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.6011 (8.28.8)

---

### Post by astrolabio on 2007-03-17
bump

same problem here

it works with gnome, with KDE i get that problem

---

### Post by redeemer on 2007-03-20
Same problem here (as mentioned in first post), on Gnome.

---

### Post by dor on 2007-03-21
Same problem here on kubuntu 6.10, with both the 8.28.8 and 8.34.8 versions

```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT
OpenGL version string: 2.0.6334 (8.34.8)

$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

$ tail /etc/X11/xorg.conf
Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option  "Composite"     "Disable"
EndSection

```

---

### Post by Waappu on 2007-03-21
Hi

You should install XGL, create own session for that and login to it.
Here is guide
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Installing_Xgl_and_Beryl](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Installing_Xgl_and_Beryl)

---

### Post by dor on 2007-03-21
Worked great, thanks!

---


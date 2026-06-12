---
title: "can i get compiz or beryl to run on this machine?"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by Choad on 2007-08-11
its got a ~900mhz pentium somethingorother... 128mb of ram and a
```
VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
```
running xubuntu 7.04. i have decided i have to try and get beryl running on it (or whatever will work)

unfortunately, i selected "compiz" from beryl-manager and now it automatically tries to load compiz when i start beryl-manager, and that just leaves me blank and i have to ctrl-alt-backspace

so firstly, how do i change the "default" in beryl-manager, and secondly is it even possible to get it working on these specs

```
richard@xubuntu-plaything:~$ beryl --replace
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
richard@xubuntu-plaything:~$ metacity --replace
The program 'metacity' is currently not installed.  You can install it by typing:
sudo apt-get install metacity
bash: metacity: command not found
richard@xubuntu-plaything:~$ xfwm4 --replace
```

---

### Post by Josko on 2007-08-15
I think that you cannot, worst thing I tryed to run Beryl on was GeForce 2 and it was running around 15-30 FPS wich is not usable.
What about compiz --replace, what it writes?

---


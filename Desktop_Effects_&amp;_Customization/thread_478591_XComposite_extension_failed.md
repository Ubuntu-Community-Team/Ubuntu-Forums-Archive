---
title: "XComposite extension failed"
date: 2007-06-19
forum: Desktop Effects &amp; Customization
---

### Post by melenor on 2007-06-19
I tried installing beryl i am running an X1800 with the restricted drivers
i ran beryl-manager from the terminal and it came up with 

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

This is what it comes up with and i have no idea how to fix it.

Edit:
i ran the beryl-manager then switched the window-manager it then came up with this.

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by maxfact on 2007-06-19
restricted drivers whit aiglx is not runnuing for beryl
yuo have must a composite manager xgl and yuo created xgl session for running beryl

excuse for my english i am italian

---

### Post by alvino on 2007-08-06
so does that mean you cant use ATI Restricted divers for beryl to run?

---

### Post by syn4k on 2007-08-07
This is an excellent question!

I just typed beryl in my Terminal and here is what I'm getting:
ray@ray-desktop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
ray@ray-desktop:~$ 

What the heck? Does anybody know anything about how to fix this?!:lolflag:

---

### Post by Methoz on 2007-08-11
I think i can help you with this problem.  It sounds like that you have the composite extension disabled, and to find out you need to check your xorg.conf file.  If it is disabled the will be a line looking somthing like this:

    option    "composite" "disable"

if this is the case then just comment out this line, restart your x server and you should be in business.

---


---
title: "Lincity-ng v2.0 Segmentation Fault"
date: 2010-04-17
forum: Gaming &amp; Leisure
---

### Post by garner_nc on 2010-04-17
Hi everyone!

Upon opening Lincity-ng v2.0, I click on new game. After selecting sandom village and "Start," lincity crashes. On the terminal, the following is displayed:

Starting lincity-ng (version 2.0)...
[/home/aleksandr/.lincity-ng] is in the search path.
[/home/aleksandr/.lincity] is in the search path.
[/usr/share/games/lincity-ng] is in the search path.
[/home/aleksandr/.lincity-ng] is the write directory.
Language is "en_US".
 fast = 9
OpenGL Mode 1024x768
 ldsv_version = 1322 
Segmentation fault

Thanks for the help,
Aleks

---

### Post by BlackShaddow on 2010-06-18
:pI had it running on lucid 64bit ...NVIDIA Driver Version:195.36.24:p


after fixing coppiz/Xinerama problems

and complete removal of "OpenCity"

:confused:Run from Consol gives : ... [for switch options as well]:confused:

==============================
ub8d10sys@Quad-6600-virt:~$ lincity-ng
Starting lincity-ng (version 2.0)...
[/home/ub8d10sys/.lincity-ng] is in the search path.
[/usr/share/games/lincity-ng] is in the search path.
[/home/ub8d10sys/.lincity-ng] is the write directory.
Language is "en_GB".
 fast = 9
* Fallback to software mode.
SDL Mode 1024x768
 ldsv_version = 1322 
Segmentation fault
ub8d10sys@Quad-6600-virt:~$
===============================
:oops::shock::shock::oops:

---

### Post by BlackShaddow on 2010-06-18
My problem also prevented "Celestia" and numerous other "little" items from running. 

After Eliminating X11, Xinerama, and numerous other Red Herrings,

I Reinstalled my NVIDIA Drivers ... also taking the opertunity to go to
NVIDIA Driver Version: 195.36.31 ! Taking all the Nvidia offered options.

:popcorn:     All now function! ...      :popcorn:

Note: Xinerama & Compiz features DO NOT work together!

---


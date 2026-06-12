---
title: "Beryl &quot;works&quot;...but nothing changes"
date: 2007-06-13
forum: Desktop Effects &amp; Customization
---

### Post by neW1_was_taken on 2007-06-13
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension                 

i have an ati radeon 9550 graphic card and 512 mb of ram.

martin@martin-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550/X1050 Series
OpenGL version string: 2.0.6334 (8.34.8)


it opens just fine but no efects,no cube...nothing.help me pls.

---

### Post by tgoose on 2007-06-13
Have you run Applications -> System Tools -> Beryl Settings Manager?

---

### Post by schorsch on 2007-06-13
Beryl on ATI graphic cards only works if you choose the XGL way (and not with AIGLX as mentioned by the beryl message!) . Take a look here:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

... if you are using feisty, of course ;)

---

### Post by revealer on 2007-06-13
try```
 sudo apt-get install beryl-manager
```
if you already have it, open it and it will show you a little red jewel in the notification bar
right click on it and choose beryl as window manager, and emerald as window decorator if you want it

---

### Post by Motoxrdude on 2007-06-13
The problem is not with beryl, but your xserver. With a ATI card, you need to use XGL, not AIGLX.
Here we go: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

---


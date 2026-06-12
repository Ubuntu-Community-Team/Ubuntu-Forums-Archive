---
title: "Unable to initialize windowing system"
date: 2011-11-14
forum: Desktop Environments
---

### Post by alnixx on 2011-11-14
Hi members, 
I need some help!
I have been using OPNET modeller (a simulation software) on Ubuntu for several years. However, after upgrading to Ubuntu 11.04 I get this message when I try to run the program from the commandline:

 * Product:   modeler (64-bit)
  * Package:   Mmi
  * Function:  Mmi_Open
  * Error:     Unable to initialize windowing system:
               X error: BadValue (integer parameter out of range for operation); serial: 359; major: 118; minor: 0; resource: 32;

Any idea what might I have caused this problem? 
Thanks for the help

---

### Post by alnixx on 2011-11-15
I have found source of the problem and solved it. The problem comes from a very surprising source. 
If I add a new keyboard layout (eg. Persian) and assign a shortcut key to it, the x window fails to initiate!
Adding a keyboard by itself is fine, however assigning a shortcut to it causes the problem. ANY shortcut key will create the error. 
It is strange and a bit alarming; a little change to Ubuntu might prevent an important software from running :(

---


---
title: "Compiz Window Manager not loading automatically in Ubuntu 9.10"
date: 2009-11-22
forum: Desktop Environments
---

### Post by ajid on 2009-11-22
I am new to **linux**. 
I am using '**Ubuntu 9.10**'. and i tried three desktop environments in my **UBUNTU**(***GNOME, KDE, XFCE***). 
Now i am using '**Gnome**' as default and my window manager is **Compiz**. 
The problem is that, when i log in, the **compiz effects** are not working.
 I have to reload my '**window manager**' by right clicking on '**compiz icon**' and selecting 
 '**Reload Window Manager**'. 
After that it is working cool. 
How to solve this?. 
Pls help me.

---

### Post by Buuntu on 2009-11-22
Hmm, that's weird, usually after you install Compiz it just automatically starts every time you log in.  Anyways, you can try adding Compiz to startup applications in System > Preferences > Startup Applications.

---

### Post by Thumper33 on 2009-11-22
I was having the same problem, and since I am completely new to Linux I was going crazy.  :)

I was able to figure out how to add it to the startup applications and that worked.  Had to get the proper command by going to PROPERTIES of the Compiz Manager and then adding that to the startup applications.

---

### Post by ZOMGxuan on 2009-11-23
You may want to try simply going to System->Preferences->Appearance, and check the Visual Effects tab. For Compiz to be the default window manager, the setting should NOT be None, i.e. it should be either Normal, Extra, or Custom. If you do see Custom listed as an option, install simple-ccsm.

---


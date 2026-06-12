---
title: "Desktop Effects - white screen?"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by Dean_Harryman on 2007-10-09
Ok, so I have been playing with ubuntu for several hours now, and I have my wireless working, and I have flash working in firefox, and my laptop is working great, except the desktop effects wont work...

I dont really car too much about them, but I would like to have the OS functioning properly.

here are my symptoms....

I go to System > Preferences > Desktop Effects, and I enable them. I get a white screen instantly. I can randomly grab at the upper right hand corner, and I can get some windows o scroll back and forth, but they are just an outline. 

so I enabled the restricted drivers.... System > Administration > Restricted Drivers Manager, and when I go to enable desktop effects, i get the following message...

"The composite Extension is not available"

What is causing this?

My System - 

HP L2000 Special Edition
AMD Turion 64 ML-37
ATI RADEON XPRESS 200M

---

### Post by luisromangz on 2007-10-09
The desktop effects config app asumes you have a AIGLX compliant driver, but you don't as ATI hasn't (yet) released a driver capable of that. You have to run compiz directly, using XGL as an intermediate layer between your AIGLX-unable X server and compiz.

There are many tutorials on the Internet on how install Xgl and make compiz run over it.

I have been using Beryl and then Compiz Fusion in a laptop almost the same as yours (Compaq is HP nowadays) and it works great using Xgl, although AIGLX support would be better.

---

### Post by Dean_Harryman on 2007-10-09
OK, so I found a guide.....

and I have chosen beryl...

I have xgl installed, and I am in an xgl session, and beryl has its diamond thing in the "taskbar" however, I am not getting any effects...... :confused:

---

### Post by Dean_Harryman on 2007-10-09
Got it to work finally.......

I am now using compiz

---


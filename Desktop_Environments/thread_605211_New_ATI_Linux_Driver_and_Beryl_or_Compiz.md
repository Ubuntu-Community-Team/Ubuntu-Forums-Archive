---
title: "New ATI Linux Driver and Beryl or Compiz"
date: 2007-11-06
forum: Desktop Environments
---

### Post by Tleslie on 2007-11-06
Hi everybody,

I am fairly new to linux. Not really familier with the desktop environment. I have seen all these great beryl and compiz videos but have not been able to get them running.

Here are my system specs.

ATI X1950 PRO 512 PCIE (Yes RV570 Chipset). 

Here is what I have done so far. 

Installed Beryl 
Installed Compiz

Installed ATI Linux 8.42.3 Drivers

I can start the beryl manager, but no beryl.. I can turn on OpenGL desktop, but nothing works. 
Emerald Themes.. Thats there as well, but will not switch themes.
I also cannot open the Desktop Effects option and get the error: Composite Extensions not Available


is there something im missing?  I have beryl running on my old ATI 320 IGP. So, Ive set it up before.  And ive read just about every tutorial I could find on these issues. 


Thanks

---

### Post by Happy_Man on 2007-11-06
Try opening a Terminal (applications --> Accessories --> Terminal) and type: ```
compiz --replace
```

See what it gives you. If you don't understand, post the output here.

---

### Post by Tleslie on 2007-11-06
/usr/bin/compiz.real: No composite extension
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manag


here is what I got..  can you explain?

---

### Post by Happy_Man on 2007-11-07
The command is "compiz --replace" with two dashes before replace. Are you sure you're using the restricted drivers for your card?

---

### Post by Tleslie on 2007-11-07
I fixed my problem... 



Restart my computer...  Got on this morning and my PC had locked up.. Did a restart and just by chance ran GLDesktop.. Noticed now it had the ati video card listed instead of the generic.  


WOOT Look at it rain!:)

---


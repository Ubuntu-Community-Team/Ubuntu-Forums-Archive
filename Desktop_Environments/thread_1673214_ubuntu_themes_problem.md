---
title: "ubuntu themes problem"
date: 2011-01-22
forum: Desktop Environments
---

### Post by jolian ramos on 2011-01-22
hi guys i want to install one of this themes for my ubuntu and i am fresh in using ubuntu so when i download them and try to add them in my system by clicking on system appearance then themes finally install i select the file but  i get error can you please help me by the right way to install this one pleaseeeeeeeeeeee?
thanks in advance 
here you are the link of the themes which i use i try all the ten approximately and i get the same error 
[http://www.pakblogger.com/10-best-themes-for-ubuntu-linux](http://www.pakblogger.com/10-best-themes-for-ubuntu-linux)

---

### Post by Krytarik on 2011-01-23
Those packages may contain complete sets of themes/icons (at least the one I tried does), so the installer isn't able to find the right one.

- place the package in the ".themes" directory of your home dir
- unpack it, right-click, "Extract here"
- do the same with the tar-package, if one appears
- enter the dir "GTK"
- move the dir you find there to the top-level ".themes" dir
- remove the rest

After that you should be able to choose the theme in the "Appearance" dialog.

You may also want to install the icons on which the theme may depend. You should also read the "readme" in the package, if one is there. The one I tried contains detailed installation instructions.

---


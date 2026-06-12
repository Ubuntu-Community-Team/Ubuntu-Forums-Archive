---
title: "How do I change the &quot;Empty Trash Bin&quot; icon?"
date: 2005-11-03
forum: Desktop Environments
---

### Post by aysiu on 2005-11-03
I changed the regular trash icon to be something else (I'm a bit of a Mac-o-phile when it comes to icons), but the "Empty Trash Bin" icon is still the old one (see attached image). Anyone know where this is located? I've poked around ~/.icons and /usr/share/icons, and I can't find it. Any help is appreciated. Thanks.

---

### Post by Freddy on 2005-11-03
If you have installed your own icon theme, they are located in /home/user/.kde/share/icons, just remove rename the icon that you don't want to use and put the new one in with exactly the same name as the previous icon had.

If it is the default icontheme in kubuntu (crystalsvg) you can find them in /usr/share/icons/crystalsvg, do the same remove/rename the icon that you want to change and put the new one in (for all sizes), but here you have to be root to work (I know that you know that but maybe others who don't reads this thread :)).   /// Freddan

---

### Post by aysiu on 2005-11-03
The problem is that I don't know what the icon is called. The icon for Trash Empty and Trash Full is not the same one used for Empty Trash Bin.

---

### Post by Freddy on 2005-11-03
Of course you right, I hadn't noticed that before. I use kxdocker with the Gtrash plugin, so I never see that menu but if you delete or rename all those styled trashicons in the kubuntus default  icontheme, you must stumble upon which icon it is.   /// Freddan

---

### Post by aysiu on 2005-11-03
I found it!
It's in /usr/share/icons/THEMENAME/SIZExSIZE/actions/emptytrash.png
```
locate trash
``` really helped me out

---


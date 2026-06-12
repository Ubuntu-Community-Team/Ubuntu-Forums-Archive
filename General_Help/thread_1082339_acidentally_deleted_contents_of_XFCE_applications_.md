---
title: "acidentally deleted contents of XFCE applications menu"
date: 2009-02-27
forum: General Help
---

### Post by richardy on 2009-02-27
Hi,
Recently installed xubuntu 8.10 and decided to make a new XFCE menu using menu editor to hold frequently used applications but i accidentally deleted the contents of the defualt XFCE aplications menu and now i cant figure out how to get it back (feel like a bit of an idiot really). Essentially when i click on the Xfce applications icon nothing happens. Anyway, how do i get the default applications menu back or am i screwed and have to make a new one from scratch. Any help would be much apreciated.

Cheers.

---

### Post by Compintuit on 2009-02-27
As long as you weren't in root, you're fine. The files that make the structure are in ```
/etc/xdg/xfce4/desktop/menu.xml
```
just replace your profile's version of the file, at 
```
~/.config/xfce4/desktop/menu.xml
```
with the contents of that file - it should reload the menu at the next reboot, if I remember correctly.

---

### Post by richardy on 2009-03-03
Hi,
Sorry for not getting back to you sooner. Thanks for the info i now have a working menu again and as always have learnt something in the process. Thanks again for your help.

Cheers.

---


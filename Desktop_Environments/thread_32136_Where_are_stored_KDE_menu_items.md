---
title: "Where are stored KDE menu items?"
date: 2005-05-06
forum: Desktop Environments
---

### Post by lucascr on 2005-05-06
Dear kubuntu users  :) 

it is quite simple to add/modify/remove items from the KDE menu using kmenuedit. 
However, it would be useful to know where these files are stored, for example, because I want to replicate the K menu created on another computer at home without going through all the point-and-click steps.
Any idea how to do it?  :-? 
Luca

---

### Post by SGC on 2005-05-06
I think it is in this file:

~/.config/menus/applications-kmenuedit.menu

---

### Post by crazybill on 2005-05-06
Perhaps search in a terminal with 

***find / -name *kmenu* -print***

---


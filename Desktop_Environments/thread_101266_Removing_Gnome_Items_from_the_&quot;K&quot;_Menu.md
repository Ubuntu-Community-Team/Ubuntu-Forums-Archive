---
title: "Removing Gnome Items from the &quot;K&quot; Menu"
date: 2005-12-09
forum: Desktop Environments
---

### Post by carney1979 on 2005-12-09
I have an install with Gnome and Kubuntu.

There are several Gnome items in my KDE "K" menu that I don't want or need in KDE, but I do want them for Gnome.

So, for an example, if I remove Gnome-terminal from my "K" menu with kmenuedit, will it also disappear from my Gnome applications menu?

If so, is there a way to make some of these items not show up in the "K" menu?

David

---

### Post by limit223 on 2005-12-09
Right click kmenu -  Menu Editor - right click the item that you don't want it - Delete

---

### Post by carney1979 on 2005-12-09
Right-clicking on the Kmenu opens kmenuedit.

Please read the original post completely. I'm not asking HOW to remove items. I'm asking if I remove Gnome items from my KDE menu, will they ALSO be removed from my Gnome menus?

David

---

### Post by carney1979 on 2005-12-09
I took the plunge and tried removing the Gnome System Monitor from my KDE "K" menu with kmenuedit.

It is gone from my "K" menu.

I booted into Gnome and it's still where it was in the Gnome menu.

So I guess if one does remove an item with kmenuedit it will not effect the Gnome menu items. 

David

---

### Post by Sokraates on 2005-12-09
AFAIK, Gnome- and K-menu are managed by different apps. So adding or removing ony app in one menu, does not change it's status in the other one.

I know since I (accidentally) removed debian menus from K-menu: it's still there in Gnome-menu. Now I try to get it back to k-menu, but that's another story ...

Anyway: if you want to make sure, add an app to k-menu, that's in gnome menu. Then remove it. it should still be there in gnome-menu.

---

### Post by limit223 on 2005-12-09
KDE and GNOME are 2 different desktop managers...that deals differnet with your applications..

---


---
title: "Resetting the kde menu"
date: 2005-11-25
forum: Desktop Environments
---

### Post by madtinkerer on 2005-11-25
Is there a simple way to reset the kde menu to default?  I installed ubunutu and then the kubuntu setup, so my kde menu is full of gnome things and half the core kde programs aren't listed.  Is there an easy way to repopulate the menu with just kde/qt applications?

Thanks

---

### Post by gingermark on 2005-11-25
Hi madtinkerer,

The short answer, I believe, is no (anyone feel free to correct me)

However, you can clean up your menu by right-clicking in it and selecting "edit menu", which brings up the KDE Menu Editor. Most apps, if not elsewhere, should be in the "debian" section, so it'll mostly be a case of drag and drop.

There is no reason not to use gtk apps in KDE though - most will look fine. Check out the "GTK Styles & Fonts" section of the Appearence tab in System Settings.

It does seem odd to me that core KDE apps aren't listed in the menu though - have you definitely installed the kubuntu-desktop metapackage?

---

### Post by teaker1s on 2005-11-25
you can config somewhere to keep them seperate-someone will tell you how as I can't remember exactly how

---

### Post by GeneralZod on 2005-11-26
[QUOTE=madtinkerer]and half the core kde programs aren't listed.[/QUOTE]


Try 

```

kappfinder

```

to see if it will restore any lost KDE apps.

---

### Post by thingy on 2005-11-26
Can you try the following:

log off KDE

mv ~/.config/menus ~/.config/menus.old

log on KDE

From my understanding...all your own modifications to the menu system are kept in that folder and so if you're looking for reverting back to the defaults then the above should do it.

---


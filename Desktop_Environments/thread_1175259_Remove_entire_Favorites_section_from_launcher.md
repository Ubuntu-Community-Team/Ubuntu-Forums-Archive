---
title: "Remove entire Favorites section from launcher"
date: 2009-05-31
forum: Desktop Environments
---

### Post by anonymous_user on 2009-05-31
Is it possible to hide or remove that menu? Since I dont use it, Id rather not have it at all.

---

### Post by Brandon Williams on 2009-06-01
You should be able to open alacarte (Preferences->Main Menu) and uncheck the favorites menu. This hides the favorites submenu from the standard gnome menu anyway. I'm not on my netbook at the moment, so I'm not certain that this will hide the favorites menu on the netbook-launcher, but give that a try first if you haven't.

---

### Post by anonymous_user on 2009-06-01
Like you said, it removed it from the Gnome menu. Though it still appears in the launcher. Any other ideas?

---

### Post by Brandon Williams on 2009-06-02
Looking at the code, it appears that netbook-launcher is hard-coded to force a Favorites submenu on you if you don't have one _and_ /usr/share/desktop-directories/Favorites.desktop exists. If you remove or rename the system Favorites.desktop file, then the Favorites menu won't be added back if you've unchecked it in alacarte.

---

### Post by ertai on 2009-06-09
This will remove the favorites-menu:

Remove the menu in the menu editor and remove /usr/share/desktop-entries/Favorites.directory

When both don't exist then the menu won't appear

---

### Post by mnrobertson on 2009-08-02
I have the opposite problem.  I just installed Netbook Remix 9.04 and was just playing around in it.  I clicked on "Main Menu" under preferences, and all the tabs disappeared, except "Favorites" (which is now empty), "Preferences" and "Administration". And when I switch to the classic Ubuntu desktop, the "Applications" menu is empty.  How do I get these back?

---


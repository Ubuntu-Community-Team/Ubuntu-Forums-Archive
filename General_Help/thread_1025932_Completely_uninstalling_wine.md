---
title: "Completely uninstalling wine?"
date: 2008-12-30
forum: General Help
---

### Post by Dudman on 2008-12-30
Hey all.

I've been trying to get Guild Wars to work on wine for a bit, but i've given up and i want to uninstall wine.

I installed wine via the provided debs(1.1.10), but the only way i could see to uninstall it was via aptitude

so i did:
 sudo apt-get remove wine
 sudo aptitude purge wine

but there's still a "wine" menu in the "applications" dropdown..

is there a way to completely remove it(other than reinstalling)?

Thanks :)

~dudMan

---

### Post by fooman on 2008-12-30
should just be a dead link.  if nothing happens when you click on wine in the menu....then its dead.

right click on "applications" and choose "edit menus"...in the "items" column,  uncheck "wine".

---

### Post by Dudman on 2008-12-30
Thanks :D

~DM

---

### Post by snova on 2008-12-30
Wine stores all of its files in ~/.wine, so remember to remove that...

---


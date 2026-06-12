---
title: "Deleting old Icons that WINE leaves behind"
date: 2007-11-19
forum: Desktop Environments
---

### Post by Borg on 2007-11-19
When 'uninstaling' a program though WINE it still leaves the folder list and icons in the WINE menu, WHY ?

How do I delete these icons and folders that are left behind.

---

### Post by PeterJS on 2007-11-19
Why? Wine does things that fall into a grey area between program data, and installation stuff the package manager should take care of. When wine creates it's shortcuts it puts them ~/.local/share/applications/wine/ which is one of the places that's read to generate the system menu. When wine is removed it has no idea what's been added there and so can't specifically remove the files, marking wine for complete should take the entire folder with it, but I seem to remember that it doesn't.

---

### Post by Borg on 2007-11-19
I'll ahve a look there but I wasn't on about deleting WINE itself just when you use the in WINE uninstaler it doesn't remove the links

---


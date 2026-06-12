---
title: "&quot;wine&quot; stupid program help"
date: 2009-02-06
forum: General Help
---

### Post by meinvateristnein on 2009-02-06
i installed a .exe program and now i have no use for it and even when i installed wine itself i still have the option of going to the program i installed ....... it has a uninstaller but when i click on it and error pops up and i cnat seem to find out how to delete it............. if anyone could tell me where this directpry is i could simply delete it ....
anyhelp would be great

---

### Post by mb_webguy on 2009-02-06
Since Wine has no real registry, you can just delete the program files.  The Wine directory is in under your home directory.  Look in ~/.wine/drive_c/Program Files for the application folder and delete it.  If the application still shows up in the Applications menu, right-click on Applications and select Edit Menus, and delete the unwanted entry.

---

### Post by meinvateristnein on 2009-02-06
thnx worked great

---


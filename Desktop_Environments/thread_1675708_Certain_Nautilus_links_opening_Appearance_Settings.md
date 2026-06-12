---
title: "Certain Nautilus links opening Appearance Settings"
date: 2011-01-26
forum: Desktop Environments
---

### Post by sidyom on 2011-01-26
When I try to open a folder via the main menu, explore a drive, show containing folder, etcetera, the appearance preferences window pops up with an error message saying "there was an error installing the selected file, "(variable folder name)" does not appear to be a valid theme". 
no matter what i've done, the appearance preferences seems to always be waiting to have a theme installed and interfering with nautilus.
any suggestions?

---

### Post by Krytarik on 2011-01-26
Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
If that is already the case, then check if the entry "gnome-appearance-properties.desktop" is listed somewhere inappropriate.

---

### Post by sidyom on 2011-01-26
Perfect, that solved everything.
the inode/directory was set for theme installer.
Thank you!

---


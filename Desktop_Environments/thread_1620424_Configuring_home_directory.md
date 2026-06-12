---
title: "Configuring home directory"
date: 2010-11-13
forum: Desktop Environments
---

### Post by adit on 2010-11-13
My home directory contains following subdirectories:
Desktop
Documents
Downloads
Music
Pictures
Public
Templates
Videos
Apart from Desktop, I don't want any of the subdirectories.  Is it safe to delete these subdirectories (they are empty).  Or is there a way to configure gnome not to show these subdirectories?

---

### Post by veli on 2010-11-13
> **adit said:**
> My home directory contains following subdirectories:
Desktop
Documents
Downloads
Music
Pictures
Public
Templates
Videos
Apart from Desktop, I don't want any of the subdirectories.  Is it safe to delete these subdirectories (they are empty).  Or is there a way to configure gnome not to show these subdirectories?

You can safely delete them.

---

### Post by mcduck on 2010-11-13
All are safe to remove, but there may be some consequences.

For example deleting the Desktop directory will result in your home directory being used as the desktop. So every single file in your home will appear on the desktop.

Deleting the Templates directory will of course prevent you from using the template functionality.

The rest shouldn't cause any issues. Some programs might look for them as default directories but you should be able to change that in each program's settings.

Anyway, if you want to hide a file or directory (without changing it's name by adding the dot in the beginning) there's an easy way. Create a file called ".hidden" in the directory where the items you wish to hide are, and then add the name of all files/directories to that file, one per line. This only works for Nautilus and some other file managers, though, so the files and directories will still appear in "ls" output.

---


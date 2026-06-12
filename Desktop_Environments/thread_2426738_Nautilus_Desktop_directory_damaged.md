---
title: "Nautilus: Desktop directory damaged"
date: 2019-09-12
forum: Desktop Environments
---

### Post by nought2 on 2019-09-12
When attempting to force the deletion of a recalcitrant a file from the /home/username folder somehow the Documents directory was inadvertently deleted. The directory contained no data, I only have links to other directories in it.

I restored it from Rubbish Bin but the Documents folder was not restored to its original place in the list of directories in the left margin of Nautilus. The Documents directory has also lost its special status. Directories listed in the margin like Home, Desktop, Downloads, Music, Pictures cannot be reordered in the list by drag and drop with mouse. The altered, damaged Documents folder can be dragged but after dropping it returns to its new place on the list.

Assistance in undoing the damage I've caused to the operation of the Desktop folder in Nautilus would be appreciated.

System is Ubuntu 18.04 LTS. 

[[IMG]https://i.postimg.cc/mrggxZ4v/Nautilus-Documents.png[/IMG]]("https://postimg.cc/mPKsCstj")

---

### Post by CatKiller on 2019-09-13
It's possible that you might be able to simply check the ~/.config/user-dirs.dirs file. It's the text file that specifies the path to those special directories.

---

### Post by nought2 on 2019-09-13
> **CatKiller said:**
> It's possible that you might be able to simply check the ~/.config/user-dirs.dirs file.Yes, that was it.

This line:
XDG_DOCUMENTS_DIR="$HOME/Documents"
had been changed to:
XDG_DOCUMENTS_DIR="$HOME/"

Reinstating correct text for the line and rebooting restored Documents directory to its proper place in the Nautilus margin.

Thank you.

---


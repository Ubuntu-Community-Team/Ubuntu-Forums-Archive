---
title: "Restoring my taskbar defaults"
date: 2010-01-09
forum: Desktop Environments
---

### Post by romber on 2010-01-09
Hi, I was trying to get a taskbar at the top of my screen to hold my essentials (clock, battery etc.) and in the process I wound up taking off my clock and battery in the lower right hand corner. Now when I try to add them back again, it just shows up as a square that says desktop. Any ideas?

Thanks

---

### Post by Zorael on 2010-01-10
I'm not sure I understand what you mean by "a square that says desktop" without first seeing a screenshot of it.

To completely wipe all plasma settings, rename or remove all files beginning with **plasma** located in **~/.kde/share/config**. If you do this in Dolphin, you may have to enable display of hidden files to see the **.kde** directory, as all files and directories beginning with a dot are hidden.

Then restart plasma by running the two following commands in succession, either in a terminal or in a run box (Alt+F2).
```
kquitapp plasma-desktop

plasma-desktop
```

---


---
title: "Lubuntu LXDE Desktop displays Home Directory"
date: 2012-04-08
forum: Desktop Environments
---

### Post by jimwims on 2012-04-08
I installed Lubuntu 11.10 yesterday.  At first the desktop display was as you would expect, no icons at all except for the bar at the bottom.  While I was installing the programs I wanted, it suddenly started displaying the contents of my home directory on the desktop.  When I click "Desktop" in the left column of the file manager, I am taken to my desktop.  If I try to delete the folders or files from my desktop, the same folder or file is deleted from my home directory.  Is there a way to get my desktop back to its normal, blank state?  Thanks for any suggestions.

Jim

---

### Post by nothingspecial on 2012-04-09
*Thread moved to **Desktop Environments**.*

---

### Post by 2F4U on 2012-04-09
Do you remember what programs were installed? Seems as if you installed a program that changed the desktop behaviour.

---

### Post by jimwims on 2012-04-09
The programs I installed were Teamviewer, fldigi (an  amateur radio digital mode program) and flrig (a companion amateur radio rig control program).  I have installed and run all of them under previous installations of different Ubuntu versions, most recently 11.04, without any problem like this.

Tnx.

---

### Post by brainwash on 2012-04-09
You can change the desktop directory by editing the value of XDG_DESKTOP_DIR in the file ~/.config/user-dirs.dirs. If the line is missing, just add:
```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

Also make sure, that the directory exists.

---

### Post by jimwims on 2012-04-09
Perfect!

Thanks very much.

Jim

---


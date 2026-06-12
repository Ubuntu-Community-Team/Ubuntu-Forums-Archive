---
title: "Unity panel has a persistant icon that will not go away"
date: 2013-01-30
forum: Desktop Environments
---

### Post by jlh68 on 2013-01-30
I downloaded an application and used it some.  When I tried to close it I could not get the icon to leave the unity panel.  I have uninstallted the application and I still have the icon.  I try to click "quit", no luck, at this point the icon is just garbage on the left unity panel and I don't know how to get the dag gone thing off of it.

---

### Post by iMac71 on 2013-01-30
one possible solution might be the following:
1) find in the /usr/share/applications directory the .desktop file of the application you wish to remove;
2) open a Terminal window by pressing CTRL-ALT-T;
3) in the Terminal window type:```
sudo rm -f 
```(there's one space after -f) but **don't press yet ENTER**;
4) drag into the Terminal window the icon of the .desktop file;
5) now press ENTER.
The icon should disappear from the Unity launcher.

EDIT: another place where you may find the .desktop file is .local/share/applications.

---

### Post by jlh68 on 2013-01-31
Easy Fix.  I just restarted my computer and it was gone.

---


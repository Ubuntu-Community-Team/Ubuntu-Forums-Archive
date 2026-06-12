---
title: "lightdm-gtk-manager login prompt persistence"
date: 2013-11-03
forum: Desktop Environments
---

### Post by dakong27 on 2013-11-03
I am running 12.10 Quantal with XFCE.  After a recent round of updates the lightdm-gtk-manager login prompt shows up on the desktop after having booted up and logged in.  I can close it manually, but would like to correct whatever's causing it to pop up again after authentication.  I checked the logs and there don't seem to be any error messages.  Can anybody point me in the right direction?  Thanks, guys.

---

### Post by Toz on 2013-11-04
It would be interesting to see what it is that is popping up. Can you post back a screenshot/capture of it?

To try to stop it from popping up after login, try clearing your sessions cache. Before you login:

1. Go to the first tty console (Ctrl+Alt+F1)
2. Log in to the text console
3. Enter the following commands:
```
cd .cache
rm -rf sessions
```
4. Log out of the text session:
```
exit
```
5. Go back to the gui login screen (Ctrl+Alt+F7)
6. Log in.

---


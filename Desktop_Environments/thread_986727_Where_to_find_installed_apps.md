---
title: "Where to find installed apps?"
date: 2008-11-18
forum: Desktop Environments
---

### Post by unsp0ken on 2008-11-18
I've only had Ubuntu for a couple of days and had a question regarding software installation and running the software. I've installed software such as tightvnc, smalldev, etc. through Synaptic. Once they are successfully installed, how do i run the software? They don't appear in the applications list. Any help would be appreciated, thanks.

---

### Post by sauce345 on 2008-11-18
I know one way to start programs on the command prompt by just typing their name.  For example if you wanted to open firefox, just type firefox and it open the program.  You might want to check under Applications -> Add/Remove to see if the program is actually installed.

---

### Post by p_quarles on 2008-11-18
> **unsp0ken said:**
> I've only had Ubuntu for a couple of days and had a question regarding software installation and running the software. I've installed software such as tightvnc, smalldev, etc. through Synaptic. Once they are successfully installed, how do i run the software? They don't appear in the applications list. Any help would be appreciated, thanks.
A few places to look:
1) Some applications are added to the menu, but not enabled there by default. To find these, right-click on the Ubuntu icon. This will allow you to edit the menu, and enable items that are currently hidden.

2) Most applications installed by Synaptic are placed in /usr/bin. If you know the exact name of an application, you can usually locate it by typing:
```
which firefox
```
This will return the full path to the program requested:
```
/usr/bin/firefox
```
3) If you *don't* know the exact name, you can search for it with the terms you do know:
```
apropos tightvnc
```
This will return the names of applications whose description includes the word "tightvnc."

---


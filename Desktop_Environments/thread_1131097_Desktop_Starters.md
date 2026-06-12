---
title: "Desktop Starters"
date: 2009-04-20
forum: Desktop Environments
---

### Post by vedhel on 2009-04-20
Hi, I'd like to create a starter (link) on the gnome desktop that, when double-clicked, runs a Windows EXE via WINE in a directory somewhere on a mounted hard disk. I can simply create a shortcut by dragging the EXE onto the desktop, it will start as well, but its working directory is not correct and it doesn't find its files. How to proceed?

Thanks!

---

### Post by MaindotC on 2009-04-20
Click:  System -> Preferences -> Main Menu.  Navigate to the directory you want to, then click "New Item".  Enter the command wine and the full path of the file you want to wine.  For example, if the file is ~/.wine/drive_c/Program Files/GTA/GTA.exe you would type in the command box:  wine ~/.wine/drive_c/Program Files/GTA/GTA.exe

---

### Post by vedhel on 2009-04-20
Thank you for your reply. I know how to create a starter, be it on the desktop (that's what I wanted) or in the menu. The problem is, the starter I create runs the program, but the working directory of the EXE is not the path the EXE is in, which in my case stops the program from functioning properly. Windows and KDE have an option that allows you to set the Working directory for an application shortcut, and I was looking for the Gnome equivalent of that.

---


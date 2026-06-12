---
title: "Can the filemanager that an application uses be changed?"
date: 2017-12-30
forum: Desktop Environments
---

### Post by justanotherjoe on 2017-12-30
Currently Im running 16.04 Ubuntu Mate but am currently running Plasma. Im not sure if this question is desktop environment specific or not but for example when opening a file from an application the file manger that is launched is different depending on the application. Can this be changed so that all applications use the same file manger? From an application when opening or saving a file I like to be able to also move or rename files as well as have access to the directory bookmarks that I set in my main file manger.

Thanks

---

### Post by Holger_Gehrke on 2017-12-30
That's not really a file-manager, it's a file dialog. The choice of using one dialog or another (or even writing your own) is made by the developer of the program. Normally a developer will use the dialog the toolkit (gtk for gnome, QT for KDE, wxwidgets or tk or ...)  he uses offers. So unless you want to get the sources and do some **major** rewriting of **all** the applications that use a dialog that you don't like, the answer is no.

Holger

---

### Post by vasa1 on 2017-12-30
Some more in [https://ubuntuforums.org/showthread.php?t=2358715&p=13633967#post13633967](https://ubuntuforums.org/showthread.php?t=2358715&p=13633967#post13633967)

---


---
title: "GNOME and Kubuntu-desktop conflict"
date: 2006-07-04
forum: Desktop Environments
---

### Post by digitalkarabao on 2006-07-04
i installed kubuntu-desktop in Ubuntu and encountered a problem.  I can no longer change the controls on the GTK themes. Trying to find a solution, I uninstalled a GTK-QT theme (I do not remember the exact name of the package). Now, I can no longer use GTK themes under KDE for Gnome applications because the option to use a GTK theme under System Settings is no longer there. Help guys.

---

### Post by Qrk on 2006-07-04
I believe you should be able to change gnome themes by starting the application in the terminal.

```
gnome-theme-manager
```

I can't think of any reason it won't work in KDE

---

### Post by aysiu on 2006-07-04
Was [this](http://www.ubuntuforums.org/showthread.php?t=161434) your original problem? If so, the solution is there as well.

---

### Post by digitalkarabao on 2006-07-05
That is exactly my problem sir. Problem is..the 'GTK Styles & Fonts' setting in KDE is no longer there. Weird. I must have deleted something which is related to that setting.

---

### Post by aysiu on 2006-07-05
Maybe this might help, then? ```
sudo aptitude update
sudo aptitude install gtk2-engines-gtk-qt
```

---

### Post by digitalkarabao on 2006-07-06
The issue was resolved by installing the gtk2-qt engine.  I installed it from the kubuntu CD.  It appears that it is not in the repositories when i reloaded my sources list. 

Thanks for the help. :)

---


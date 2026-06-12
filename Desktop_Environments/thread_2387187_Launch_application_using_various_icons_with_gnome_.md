---
title: "Launch application using various icons with gnome desktop shortcut"
date: 2018-03-15
forum: Desktop Environments
---

### Post by nlee2 on 2018-03-15
In ubuntu 17.10 gnome desktop, I made desktop shortcuts to launch an application with different parameter on the exec line. Each desktop shortcut uses a different icon to represent the parameter being passed. The proper custom icon is displayed in Activities and Favorites but when I launch the desktop shortcut it is the generic application icon that is displayed. 

How do I create a shortcut that will use a different icon to distinguish between each exec parameter?

---

### Post by kostkon on 2018-03-16
You could try the following, it might make a difference:

Append the --class parameter to your Exec entry in order to set a custom WM_CLASS for each .desktop file, e.g.:
```
Exec=my_executable --class=MyCustomClass1
```
and also add the following line to each .desktop file:
```
StartupWMClass=MyCustomClass1
```

Hope that helps

---

### Post by nlee2 on 2018-03-16
Thanks for the info. Unforunately vncviewer aka my_executable does not support --class parameter. What to do?

edit

Got it working by using xprop to get the vm_class and use that class in StartupWMClass.

---


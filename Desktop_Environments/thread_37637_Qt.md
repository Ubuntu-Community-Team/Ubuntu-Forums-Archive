---
title: "Qt"
date: 2005-05-27
forum: Desktop Environments
---

### Post by thagame on 2005-05-27
im trying to compile a package that isnt in kubunutu package list and i keep getting this error 

> checking for Qt... configure: error: Qt (>= Qt 3.0.3) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

i looked in synaptic and i have basically every qt package installed and i have essentials install also. anyone else getting this error

---

### Post by shakin on 2005-05-27
Make sure you have the various qt -dev packages.

You also might need to add a path to qt for the configure script, something like --with-qt=/path/to/qt

---


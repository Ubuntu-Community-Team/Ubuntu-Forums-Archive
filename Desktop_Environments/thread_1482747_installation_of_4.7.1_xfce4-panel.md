---
title: "installation of 4.7.1 xfce4-panel"
date: 2010-05-13
forum: Desktop Environments
---

### Post by morgengenuss on 2010-05-13
hey everyone.
tried to compile and install xfce4-panel version 4.7.1 today.
basically everything went fine, built and installed garcon-0.1.1, libxfce4ui-4.7.1, exo-0.5.2 and upgraded xfconf without problems.

when first trying to install there was a stupid error saying that the icon theme cache was in both exo and the panel package, so i had to uncomment a few lines from the panel make file to let it install.

after all that however it wouldn't start stating that:
```
xfce4-panel
xfce4-panel: error while loading shared libraries: libxfce4panel-1.0.so.3: cannot open shared object file: No such file or directory
```

i checked and that file was
a) in the package i built
b) in the /usr/local/lib

also exo complained
```
libexo-1.so.0: cannot open shared object file: No such file or directoryFailed to load module: /usr/lib/gio/modules/libexo-module-1.so
```
even though the file was actually in the place it was looking for.


has anyone else here tried to install the new xfce4-panel successfully? would be interested to fix this problem. thanks in advance!

---


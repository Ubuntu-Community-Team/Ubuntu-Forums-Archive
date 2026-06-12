---
title: "KDE4 libkdeprint.so.5-Issue"
date: 2007-11-15
forum: Desktop Environments
---

### Post by annaeus on 2007-11-15
Hello,

some days ago i could start any KDE4-Programm and it was fine.

Since yesterday i`ve a little problem here:
parley: error while loading shared libraries: libkdeprint.so.5: cannot open shared object file: No such file or directory

The file doesn`t exist, but there is a file called /usr/lib/kde4/lib/kde4/libkdeprint_part.so

ln -s /usr/lib/kde4/lib/kde4/libkdeprint_part.so /usr/lib/kde4/lib/kde4/libkdeprint.so.5

didn`t solve the problem too.

Any ideas?

Thanks.

---


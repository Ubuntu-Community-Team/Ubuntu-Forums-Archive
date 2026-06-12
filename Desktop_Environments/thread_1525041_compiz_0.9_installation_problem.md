---
title: "compiz 0.9 installation problem"
date: 2010-07-06
forum: Desktop Environments
---

### Post by tezer on 2010-07-06
Hi,
I am trying to install Compiz 0.9. I downloaded the files and unpacked them. The INSTALL says I need to run autogen.sh, but there is no such a file in the folder.
Any idea what to do?

---

### Post by kybl on 2010-07-06
Try this: ```
mkdir build
cd build
cmake ..
```
and after then make and sudo make install.

---


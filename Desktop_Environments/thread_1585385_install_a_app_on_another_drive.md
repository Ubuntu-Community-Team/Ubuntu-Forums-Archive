---
title: "install a app on another drive"
date: 2010-09-30
forum: Desktop Environments
---

### Post by Wakawakamush on 2010-09-30
hi,

i need to install a app on another partion because its 10 gb and i only have 20 gb for ubuntu. how do i do that?

If this thread is posted in a wrong section, please tell me.

---

### Post by sharathcshekhar on 2010-09-30
If you are compiling the package from source, you can pass the prefix=/path/to/install argument to ./configure and then compile the package and install it with make and make install.
This will install the package in what ever partition you have mentioned as prefix(of course it has to be mounted) 
If you are installing from a binary, a .deb file, there is probably no way to do it.

---


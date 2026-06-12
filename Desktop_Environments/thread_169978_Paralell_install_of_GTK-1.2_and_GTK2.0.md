---
title: "Paralell install of GTK-1.2 and GTK2.0"
date: 2006-05-03
forum: Desktop Environments
---

### Post by todoporron on 2006-05-03
Hi.

I have GTK+ 2.0 installed. However, some software that I need to use, uses GTK 1.2. I read that it is possible to have two versions of GTK+, Which is the best (and safest) way to get this? Sorry I'm new to linux and do not know many things. 

Thanks.

---

### Post by yabbadabbadont on 2006-05-03
Just install the software that you wish to use with apt-get or synaptic and they will handle pulling in any required dependencies automatically for you.

---

### Post by todoporron on 2006-05-04
[QUOTE=yabbadabbadont]Just install the software that you wish to use with apt-get or synaptic and they will handle pulling in any required dependencies automatically for you.[/QUOTE]


Well, that's the point. This apps can not be installed via apt-get or synaptic. You have to download it and compile-install. I'm not sure how to do the compilation-install. Thank you.

---

### Post by louis_nichols on 2006-05-04
Sure they can run together. In Linux, backwards compatibility is much easier than in windows, because all runtime libraries have their version number included in them. So in your Ubuntu setup,, you can safely install gtk1.2 and gtk2.0 and every app will know which one to use. No fuss about that.

As for compiling. If, say, you are compiling an app that requires gtk1.2, then you need to install via synaptic the package libgtk1.2-dev and any dependencies it may require. Likewise, for gtk2.0 you will install libgtk2.0-dev. Again, no harmful mixture. The compilation itself is usually explained in every source code tarball inside a file called INSTALL or sometimes in the README itself. The general steps are:

1. Uncompress the source and go into the directory
2. run ```
./configure
``` inside this folder
3. If configure runs without errors, run ```
make
```
4. If make runs without problems, run ```
sudo make install
``` to actually install the app. Actually, my recommendation would be to install the package named checkinstall and, in this last step, use:

```
 sudo checkinstall
```

This will create a deb package of the app and install it. This package will run on your machine, but won't have any data included about dependencies so it's not good for distributing. The advantage is that later it will be easier to uninstall, and generally manage as an app.

---

### Post by yabbadabbadont on 2006-05-04
[QUOTE=todoporron]Well, that's the point. This apps can not be installed via apt-get or synaptic. You have to download it and compile-install. I'm not sure how to do the compilation-install. Thank you.[/QUOTE]

OK, now I understand your problem.  Just install gtk 1 using:

sudo apt-get install libgtk1.2-dev

That should pull in everything you need to build and run a program against gtk 1.2.

---


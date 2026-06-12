---
title: "Help Installing Plasmoid!"
date: 2009-06-01
forum: Desktop Environments
---

### Post by izizzle on 2009-06-01
I downlaoded the YASP Sytem Monitor from [HERE]("http://www.kde-look.org/content/show.php?content=94144&forumpage=9"), but I need help installing it. I have no idea how to install it.

Thanks.

---

### Post by izizzle on 2009-06-02
Bump...

---

### Post by krazyd on 2009-06-03
read the INSTALL file inside the download.

instead of the 'sudo make install' step, try 'sudo checkinstall'

you'll have to install checkinstall for this (sudo apt-get install checkinstall). this will create a package for you so you can easily uninstall the plasmoid later if you want.

---

### Post by izizzle on 2009-06-03
When I do a sudo make install, I get the following error: ```
/home/imran/Desktop/yasp-1.3/src/yasp/file.cpp: In member function ‘QStringList Yasp::File::tail(const int&)’:
/home/imran/Desktop/yasp-1.3/src/yasp/file.cpp:79: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.3/README.Bugs> for instructions.
make[2]: *** [src/yasp/CMakeFiles/yaspd.dir/file.o] Error 1
make[1]: *** [src/yasp/CMakeFiles/yaspd.dir/all] Error 2
make: *** [all] Error 2
```

---

### Post by krazyd on 2009-06-03
I'd ask on the kde-look page..

---


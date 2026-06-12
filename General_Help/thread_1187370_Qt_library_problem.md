---
title: "Qt library problem?"
date: 2009-06-14
forum: General Help
---

### Post by z0diac on 2009-06-14
Hello,

I just installed QtCreator.I made an extreme simple project, the first time with just a label and in my second try I didn't change anything, I directly tried to run the program.Both times I get the following error - "error: collect2: ld returned 1 exit status".That didn't give me any information, so I tried to compile the two "programs" with the use of their automatically generated makefiles.Again, I get the same errors:
> z0diac@wolverine:~/Desktop/HelloWorld$ make
g++ -Wl,-O1 -o HelloWorld main.o mainwindow.o moc_mainwindow.o    -L/usr/lib -lQtGui -lQtCore -lpthread
/usr/bin/ld: cannot find -lQtGui
collect2: ld returned 1 exit status
make: *** [HelloWorld] Error 1
I googled it, but couldn't find a solution.Thanks in advance.

:)

---

### Post by Mariane on 2010-02-08
You seem to have some missing libraries. 
Try searching for it directly:
```

sudo apt-cache search lQtGui

```

If you see it, you can install it by typing:
```

sudo apt-get install lQtGui

```

If you don't see it, search qt and install top-level stuff, they will usually bring down the rest. For example if you install designer it will bring the required libraries. 

Mariane

---


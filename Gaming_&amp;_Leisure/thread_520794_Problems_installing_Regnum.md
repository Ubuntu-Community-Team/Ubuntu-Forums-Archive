---
title: "Problems installing Regnum"
date: 2007-08-08
forum: Gaming &amp; Leisure
---

### Post by SquEarle on 2007-08-08
I recently heard about Regnum, and I've been having trouble installing it.  I think I'm making an idiot's mistake, but i can't figure it out.  After downloading, and unpacking I type > /media/sda2/regnum$ ./rolauncher 

and it shoots back:
> ./rolauncher: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

I tried make and configure as well, but there aren't any make or configure files.  So the next step was I linked the libgtk-x11-2.0.so.0 file to the directory, but i get the same error.

oh, and I'm running feisty fawn on an AMD64 system.

Thanks in advance for any help!

---

### Post by misconfiguration on 2007-08-09
```
sudo apt-get install --reinstall libgtk2.0-0
```

---


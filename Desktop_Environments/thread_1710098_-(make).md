---
title: "-(make)"
date: 2011-03-19
forum: Desktop Environments
---

### Post by smss on 2011-03-19
Hello.
 How to remove a program by the command 
```

./configure
make
sudo make install 
```
installed??
Best Regards
***smss***

---

### Post by sisco311 on 2011-03-19
In most cases **sudo make uninstall** will do the trick.

But to make it easier, instead of **sudo make install**, you should use **sudo checkinstall**. Then you can remove the installed package via Synaptic or a terminal (**dpkg -r package** or **apt-get remove package**). See: [uhelp]community/CheckInstall[/uhelp].

---


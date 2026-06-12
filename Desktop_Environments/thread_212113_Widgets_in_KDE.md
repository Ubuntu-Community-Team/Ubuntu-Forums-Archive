---
title: "Widgets in KDE"
date: 2006-07-09
forum: Desktop Environments
---

### Post by srunni on 2006-07-09
Hey

I've heard quite a bit about widgets in KDE and seen some screenshots. How exactly do you get these widgets? I looked in the package manager and didn't find anything, even with all the repositories on. Does anyone know where I can find these widgets?

Thanks in advance.

---

### Post by aysiu on 2006-07-09
*superkaramba* is what you want, and you may need to [enable extra repositories](http://www.psychocats.net/ubuntu/sources) for that.

---

### Post by srunni on 2006-07-09
I downloaded SuperKaramba from netdragon.sourceforge.net, as I couldn't get it to show up in the package manager. When I used the ./configure command in the extracted folder, everything seemed to be working until I got the error 

configure: error: Can't find X includes. Please check your installation and add the correct paths!

Does anyone know how I can fix this?

---

### Post by aysiu on 2006-07-09
Yes. [Enable extra repositories](http://www.psychocats.net/ubuntu/sources). Then ```
sudo aptitude update
sudo aptitude install superkaramba
```

---

### Post by srunni on 2006-07-09
Thanks a lot.

Would you happen to know the name of a widget that displays system info, like CPU, memory and network load, etc?

---

### Post by Jucato on 2006-07-09
[http://www.kde-look.org](http://www.kde-look.org) has a lot of Superkaramba themes available for download. They come in .tar.gz archives. All you need to do is to download them and extract them to a convenient place/folder, then either double-click on the .theme file that comes with it or manually look for it using Superkaramba's Add Theme button (of course you have to launch Superkaramba first if you do this the 2nd way).

---


---
title: "creating desktop shortcut with root permissions in ubuntu linux"
date: 2010-10-20
forum: Desktop Environments
---

### Post by metallica1973 on 2010-10-20
I am using Lubuntu 10.10 and have installed my application that I need. What I need is a link to the desktop that will execute the program from the /usr/share/test directory. When I execute the program I need to use "Sudo" in order to run in. So my questions is how would I add a symbolic link the desktop with the appropriate permission to run the executable without compromising security.
I tried everything but cannot get it to execute under ubuntu:

[PHP][Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=sudo /usr/share/test/test_scripts/test
Terminal=true
Name=Test
Comment=Test network vulnerability scanner
Icon=/usr/share/test/html/images/test_icon.png
Category=Application;  [/PHP]

---

### Post by nilarimogard on 2010-10-20
Modify this:

```
Exec=gksu /usr/share/test/test_scripts/test
```

---

### Post by metallica1973 on 2010-10-20
it still does work. It does nothing.

---


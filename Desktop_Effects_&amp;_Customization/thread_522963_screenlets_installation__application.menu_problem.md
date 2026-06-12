---
title: "screenlets installation : application.menu problem"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by maduranga on 2007-08-11
Hello... I have download screenlets latest version and now i'm trying to install it.**sudo make install** work perfectly without any errors. But when I gave the command "**sudo make menu**" (as described in readme) it gives following error in terminal:

[B]maduranga@001-FeistyFawn:~/screenlets-0.0.9$ sudo make menu
make -C desktop-menu
make[1]: Entering directory `/home/maduranga/screenlets-0.0.9/desktop-menu'
cp /home/maduranga/.config/menus/applications.menu /home/maduranga/.config/menus/applications.menu.bak
cp: cannot stat `/home/maduranga/.config/menus/applications.menu': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/maduranga/screenlets-0.0.9/desktop-menu'
make: *** [menu] Error 2
maduranga@001-FeistyFawn:~/screenlets-0.0.9$ [/B]


this is the first time i'm going to install a software manually... so pls someone help me. thanks

---

### Post by maduranga on 2007-08-11
ok. i got it working bye copying the needed file to the needed location.. now it works,,,!!! great!!!

---


---
title: "dell inspiron M5030 touchpad not responsive"
date: 2012-06-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xaegis on 2012-06-03
I an currently running Ubuntu 12.04 on a Dell inspiron M5030 and have had problems with the touchpad not responding after it gets to the desktop screen. (it only functions in ubuntu 2D mode but that is another issue entirely)
It turns out it is disabled by default on my installation, the way I fixed it was found [HERE]("http://askubuntu.com/questions/65736/touchpad-not-working-on-dell-xps-l501x").

    Install dconf-tools Install dconf-tools

    Launch it dconf-editor

    Search for: /org/gnome/settings-daemon/peripherals/touchpad/

    Check "touchpad-enabled"



HTH

---


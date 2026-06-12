---
title: "xfwm4 doesn't save compositing settings"
date: 2009-07-14
forum: Desktop Environments
---

### Post by b.a.w on 2009-07-14
I am running Xubuntu 9.04 installed from the alternate cd. Everything is running fine except for an issue with the compositing settings. I can enable composting fine, but it seems I am stuck with default settings from somewhere. I want all the opacity settings to be 100% opaque. The xfce-settings-manager says that the are 100%, but they are not. The xfwm4.xml file in my home directory that corresponds to the settings-manager contains the same info. I am lost on where xfwm4 is reading its settings from if it's not from the file in my home. Any insight on this problem would be greatly appreciated. Thank you.

---

### Post by b.a.w on 2009-07-14
Nevermind, I just found my answer on the Xfce bug list. It seems a theme can state the compositing setting values that override the settings in the settings-manager. I found this information at this link [http://bugzilla.xfce.org/show_bug.cgi?id=3927](http://bugzilla.xfce.org/show_bug.cgi?id=3927) if anyone else is experiencing this problem also.

---

### Post by cyb3rkn19ht on 2009-11-14
I used xfwm4 --replace to get my window manager and all it settings back.

---


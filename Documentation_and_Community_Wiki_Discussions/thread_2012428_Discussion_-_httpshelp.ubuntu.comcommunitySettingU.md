---
title: "Discussion - https://help.ubuntu.com/community/SettingUpConky"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by Elfy on 2012-06-29
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky)

Support threads should be posted in normal forums.

Thank you.

---

### Post by kdford on 2012-12-10
Using Lubuntu 12.10

I followed the instructions (the wiki points to .config/lxsession/LXDE/autostart but the actual file you need to manipulate is .config/lxsession/Lubuntu/autostart) and although conky launches properly, my panel does not launch.  If I remove the autostart file, the panel launches fine.

When I have the autostart in place, and the panel does NOT launch on login, if I subsequently execute ```
lxpanel
``` from the command line, the panel appears but it is themed in a dramatically different way, and contains some different applets than what my regular panel has..

Any thoughts?

p.s. I submitted an edit to the page to update from LXDE -> Lubuntu for location of the autostart file.. Hopefully this is accurate as when I put it in the LXDE folder, it appeared to be completely ignored upon login.

---

### Post by cL0h on 2014-02-05
I am assuming there is a typo in the code snippet for autostarting a conky script. In this code sample:


```
mkdir -p ~/.config/lxsession/Lubuntu/
touch ~/.config/lxsessions/Lubuntu/autostart
leafpad autostart
```

The first line refers to a folder called ***lxsession***
The second line refers to a folder called ***lxsessions***

Thanks
C.

---

### Post by Elfy on 2014-02-05
It's a wiki - you can edit it yourself :)

---


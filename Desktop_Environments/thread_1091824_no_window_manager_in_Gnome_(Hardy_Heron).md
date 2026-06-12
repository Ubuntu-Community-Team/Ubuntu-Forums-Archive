---
title: "no window manager in Gnome (Hardy Heron)"
date: 2009-03-09
forum: Desktop Environments
---

### Post by Pollywoggy on 2009-03-09
I have Hardy Heron installed and in Gnome, I do not have the top window bar on my apps with the default settings but if I go to System > Preferences > Appearance > Visual Effects and set it from "Normal" to "None", the top bar on the windows appears so that I am able to move or resize the windows.  I do not have this problem on Intrepid and the default settings work. 

Am I missing an important Gnome package?  Perhaps if I installed a package that is missing, I would be able to use the default ("Normal") setting.

thanks

---

### Post by cubeist on 2009-03-09
sounds like the window borders disappear only when compiz is running... this is an easy fix... open the compiz config settings manager, open the **window decorations** panel and in the field called **command** type:
```
gtk-window-decorator --replace
```

---

### Post by Pollywoggy on 2009-03-09
> **cubeist said:**
> sounds like the window borders disappear only when compiz is running... this is an easy fix... open the compiz config settings manager, open the **window decorations** panel and in the field called **command** type:
```
gtk-window-decorator --replace
```

Thanks, that might be it.  I looked for the configurator and it was not installed, so I installed it.  Perhaps after I logout and login again, things will work correctly.

---


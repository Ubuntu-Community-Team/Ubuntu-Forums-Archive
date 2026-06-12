---
title: "Compiz trouble (glx ext texture missing)"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by obbe on 2007-10-21
Hi, i'm on gusty gibbon and i'm frustrated with the following issue, after having uninstalled and installed compiz again ( i was trying to install the GIT version but i failed), i'm not able to start it anymore, if i try to activate it from system-preferences-apparance a message showing "desktop effects could not be enabled" appears, and if i try launching it by a terminal typing 
```
compiz --replace
```
that's what i get:
```
compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"
compiz (core) - Fatal: [COLOR="black"]GLX_EXT_texture_from_pixmap is missing[/COLOR]
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
```

any solution? :( thanks

---

### Post by luisromangz on 2007-10-21
What graphic card are you using? If it's an ATI card, the standard way for Compiz to work that is using AIGLX won't work, you'll have to use it on top of XGL.

---

### Post by obbe on 2007-10-21
yes i'm using an ATi card, so what can i do? is there a guide or something like that to fix this trouble making XGl working? what's strange is that untill i unistalled it it worked..
i forgot, the 3d rendering is obviously activated

ok, it seems to be solved, i followed this guide [http://taninorulez.wordpress.com/2007/10/19/the-composite-extension-is-not-available-ubuntu-gusty-gibbon/](http://taninorulez.wordpress.com/2007/10/19/the-composite-extension-is-not-available-ubuntu-gusty-gibbon/)

---


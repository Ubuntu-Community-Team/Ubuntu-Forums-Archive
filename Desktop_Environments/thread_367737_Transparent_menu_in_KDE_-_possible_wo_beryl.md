---
title: "Transparent menu in KDE - possible w/o beryl?"
date: 2007-02-22
forum: Desktop Environments
---

### Post by martinrandau on 2007-02-22
The title says it. Can I have the menu in KDE transparent, just like the panel can be?

---

### Post by esaym on 2007-02-22
Yes I don't know the details but it depends on the theme you are using.  See ```
kcontrol
``` Appearance & Themes-->Style-->Effects-->Menu Effect

---

### Post by oobuntoo on 2007-02-22
> **martinrandau said:**
> The title says it. Can I have the menu in KDE transparent, just like the panel can be?

Yes. There are two ways.
1. Fake transparency.
System Settings->Appearance->Style. Click on "Effects" tab, tick "Enable GUI effects". On the drop-down list for "Menu effect", choose "Make Translucent".

2. Real transparency and shadow with KDE built-in composite manager (NOT really stable, need tweaking of xorg.conf file, and depends on video card and driver used).

System Settings->Window Behavior. Click on "Translucency" tab and tick "Use translucency/shadows" and just play with the settings.

Not sure if the second option will give you menu transparency. You might want to search the forum on KDE built-in composite manager for more info.

---


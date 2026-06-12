---
title: "Replacing The Default Theme"
date: 2009-12-20
forum: Development CD/DVD Image Testing
---

### Post by Yogotiss on 2009-12-20
I'm working on creating my own some what version of Ubuntu using Reconstructor and Remastersys. These two program work great I just wanted to know if anyone knew how to change the old default theme when running Ubuntu live to a theme that I want as default.

---

### Post by k@e on 2009-12-20
Change these gconf keys according to your likes:

For window border: */apps/metacity/general/theme <theme_name>*
For GTK elements: */desktop/gnome/interface/gtk_theme <theme_name>*
For icon theme: */desktop/gnome/interface/icon_theme <theme_name>*

Replace the bracket with the theme name you want to have, e.g. Clearlooks. Make sure the theme is installed and can be found in */usr/share/themes*, while icon themes must be located in */usr/share/icons*.

In order to make the theme default for any user of your live distro, use these lines _in your chroot environment_ to set the keys above as default, e.g.:

```
gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type string --set /desktop/gnome/interface/gtk_theme <theme_name>
```

---


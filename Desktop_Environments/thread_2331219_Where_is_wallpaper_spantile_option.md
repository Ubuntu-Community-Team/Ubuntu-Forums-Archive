---
title: "Where is wallpaper span/tile option?"
date: 2016-07-19
forum: Desktop Environments
---

### Post by swilson2 on 2016-07-19
Either I'm losing my mind or I swear there used to be a drop down box on that lets you span your desktop wallpaper across dual monitors.  Where did it go??  I have a cookie cutter ubuntu 16.04 fresh install and there's no way to span a wallpaper.

Help!!!

---

### Post by mcduck on 2016-07-21
Well, looks like Gnome developers have once again decided a feature no not be soemthing users should have access to... :D

Anyway, even if they are now hidden from the UI, the options till exist in gsettings. So you can use dconf-editor or gsettings to change the wallpaper options.

For gsettings:
```

gsettings set org.gnome.desktop.background picture-options spanned

```

---

### Post by Frogs Hair on 2016-07-21
Still in appearance settings here .

---


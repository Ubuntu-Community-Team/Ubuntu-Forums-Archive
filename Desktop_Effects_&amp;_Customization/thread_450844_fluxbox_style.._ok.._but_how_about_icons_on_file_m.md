---
title: "fluxbox style.. ok.. but how about icons on file mngr?"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by smokinjoe on 2007-05-21
ok.. you're using fluxbox..means that you don't see a lot of icons since it's almost all about command and thing..

anyway my question is: how can I change icon themes on fluxbox?

the icons that appear in thunar for example.. they must use some default icon theme..

so how can i apply theme icons on fluxbox? since my main goal is to full customize my desktop

---

### Post by yabbadabbadont on 2007-05-21
In your ~/.gtkrc-2.0 file:
```
gtk-icon-theme-name="YourIconThemeNameHere"
```

Edit: This is a useful resource to read: [http://developer.gnome.org/doc/API/2.0/gtk/GtkSettings.html](http://developer.gnome.org/doc/API/2.0/gtk/GtkSettings.html)

---

### Post by smokinjoe on 2007-05-22
thanks!!!!

---


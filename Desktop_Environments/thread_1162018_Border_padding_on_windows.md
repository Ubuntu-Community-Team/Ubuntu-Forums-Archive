---
title: "Border padding on windows"
date: 2009-05-17
forum: Desktop Environments
---

### Post by Vostrocity on 2009-05-17
Is it possible to change the size of the border padding like you can in Windows? I want to get rid of the extra line on the left and right of the window OS X style.

---

### Post by gettinoriginal on 2009-05-17
You don't say what window manager you are using, but it can be adjusted in CompizConfig Settings Manager under Window Decoration, and it can also be changed if using emerald.  I am sorry, but I don't know how to do it in metacity.

---

### Post by mcduck on 2009-05-18
> **Vostrocity said:**
> Is it possible to change the size of the border padding like you can in Windows? I want to get rid of the extra line on the left and right of the window OS X style.

Assuming you are using Metacity themes for your window borders, no, it's not customizeable (apart from editing the theme code by hand). I suggest just getting a theme you like from gnome-look.org and using that..

---

### Post by Vostrocity on 2009-05-18
Sorry I don't really know what I use, either Metacity or Compiz. I don't think I ever changed it from the default (Metacity) but the Compiz settings to work.

---

### Post by mcduck on 2009-05-19
> **Vostrocity said:**
> Sorry I don't really know what I use, either Metacity or Compiz. I don't think I ever changed it from the default (Metacity) but the Compiz settings to work.

If you haven't changed anything yourself, and use the desktop effects that means you are using Compiz as your window manager, and Compiz uses gtk-window-decorator as it's window decoration plugin. Gtk-window-decorator uses Metacity themes.

---

### Post by gettinoriginal on 2009-05-19
Then to change the window border you need compizconfig-settings-manager (install it if you haven't already), then System, Preferences, CCSM, Effects, Window Decoration (check it if it is not already), then click the window icon.  You can play with the border settings there, they will change as you move the cursors around, so you can always hit the broom to take it back to default. 
[ATTACH]114317[/ATTACH]
You may want to change the command to
```
gtk-window-decorator --replace
```
Also installing "fusion-icon" is a good way to know and to control the window manager and window decorator

---


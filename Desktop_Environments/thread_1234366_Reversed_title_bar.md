---
title: "Reversed title bar"
date: 2009-08-07
forum: Desktop Environments
---

### Post by pwoolcoc on 2009-08-07
Ubuntu 9.04

I tried the Mac4Lin theme, and decided to go back to the default theme.  However, after I uninstalled the theme, the buttons & program icon in the title bar of an application window (buttons being close, maximize, minimize) are reversed, like they were for the Mac4Lin theme.  I have looked through the preferences and have not seen an option to change this, anyone have an idea?

---

### Post by asmoore82 on 2009-08-07
either in a Terminal or Alt+F2, run
```
gconf-editor
```
and edit the key "/apps/metacity/general/button_layout"
it should be "menu:minimize,maximize,close"

A "one-shot" fix-it would be this command:
```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "menu:minimize,maximize,close"
```

---

### Post by pwoolcoc on 2009-08-08
Thanks, that did the trick!

---


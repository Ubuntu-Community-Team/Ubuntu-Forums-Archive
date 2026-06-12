---
title: "Win Key on Ubuntu 10.04 open Applications menu"
date: 2010-05-23
forum: Desktop Environments
---

### Post by fss007 on 2010-05-23
- open terminal and type gconf-editor
- apps -> metacity -> global_keybinding and look for panel_main_menu
- right click and edit, change value to "Super_L" without the quote.

and That's it!

---

### Post by wojox on 2010-05-23
Or you could just run this in the terminal:

```
gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"
```

---

### Post by texaswriter on 2010-05-23
On my laptop: Alt-Fn-F1
On my PC: Alt-F1

That brings up the application menu just fine.

---


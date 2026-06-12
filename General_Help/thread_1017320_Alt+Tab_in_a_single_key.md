---
title: "Alt+Tab in a single key"
date: 2008-12-20
forum: General Help
---

### Post by hardysummer on 2008-12-20
How do I change a key to be Alt+Tab?

Since the Windows key (between Ctrl and Alt) is useless, how do I map it to be Alt+Tab?

---

### Post by jerome1232 on 2008-12-20
That depends on if you use compiz or not.

If you do use compiz then you can change the keybinding for whatever application switcher you are using to be Windows key+tab, just install compizconfig-settings-manager from synaptic, logout then log back in, goto System-Preferences-CompizConfig Settings Manager

If not then you'll be able to find it under System-Prefrences-Keyboard Shortcuts, it's called "Move between Windows with popup"

---

### Post by fubbleskag on 2008-12-20
assuming you are not using metacity as your window manager (default), open the gnome configuration editor (gconf-editor) and find **/apps/metacity/global_keybindings/switch_windows** and change the value to *<Super>*

---

### Post by laceration on 2008-12-21
I'm not sure you can simply get 1 key to work as 2.  If the above methods do not work, there is a more complicated solution.  From synaptic get a program called xautomation.  Then you would have to write a script like this:
```

#!/bin/bash
xte "keydown Alt_L";sleep 1;xte "key Tab"

```
save the file and don't forget to make it executable.  Then you would have to set the Super key to run the script.

---


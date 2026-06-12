---
title: "Turn off the Bubble"
date: 2006-04-26
forum: Desktop Environments
---

### Post by eppoh on 2006-04-26
If I knew what is was officially called, I could probably find out myself- but I don't.
I want to turn off that annoying little bubble helper that pops up every time I place my mouse over a menu or  icon. Ya know it gives a little helper preview of what the icon represents- but it gets in the way of seeing things around it.

---

### Post by AndyCampbell on 2006-04-26
Try this: gconf -> / > apps > panel > global > tooltips_enabled, uncheck

---

### Post by eppoh on 2006-04-26
[QUOTE=AndyCampbell]Try this: gconf -> / > apps > panel > global > tooltips_enabled, uncheck[/QUOTE]I don't find gconf.. Where is that?

---

### Post by Ramses de Norre on 2006-04-26
Do this in terminal: ```
gconf-editor /apps/panel/global/tooltips_enabled
```
It's also in the menu somewhere as configuration editor, I don't know where exactely and I'm not in ubuntu now so I can't check.

---

### Post by eppoh on 2006-04-26
That worked! Great thanks. Don't know why the configuration editor is not in my menus anywhere?

---

### Post by AndyCampbell on 2006-04-26
Menu/System Tools/Configuration Editor.  I assume your using Gnome.  If it's not in your menu then you may need to go to Menu/System Tools/Applications Menu Editor and add it.

---


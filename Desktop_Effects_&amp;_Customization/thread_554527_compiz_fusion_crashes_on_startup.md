---
title: "compiz fusion crashes on startup"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by Metallion on 2007-09-19
Today suddenly compiz decided to crash as soon as I try to start it.

this is the output it gives me in a terminal:
```
 
A handler is already registered for the path starting with path[0] = "org"
inotify_add_watch: No such file or directory
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (shift) - Warn: No compatible text plugin loaded.
/usr/bin/compiz: line 777:  6860 Segmentation fault      (core dumped) $*
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "switch_windows"

```

Has anone got an idea what is the cause of that? I  made one update to some library today but I really just ran the update manager without really looking what it was updating. Has anyone got a clue what might be wrong here? Maybe a certain plugin I should disable?

---


---
title: "Error activating XKB configuration"
date: 2009-09-26
forum: Desktop Environments
---

### Post by rucadulu on 2009-09-26
**Error activating XKB configuration**             
                                                                Has anyone seen this error before, if so how was it resolved ?

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10600000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

r@ubuntu1:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "us", "", ""
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "us", "", ""

r@ubuntu1:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [aa]
 options = []
 model = 

Thank you for any help that you can provide. Russell.

---


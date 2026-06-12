---
title: "Keyboard layout switching not working when using Russia Phonetic"
date: 2008-03-01
forum: Desktop Environments
---

### Post by Shutdownrunner on 2008-03-01
To start with sth: 

xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "pl", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "pl,de,ru", ",,phonetic", "grp:alts_toggle"

The problem is that after I reboot I can't use Russia Phonetic keyboard layout in Gnome. Keyboard layout applet lets me choose between Polish ang German layout, but Russian despite being present in popup menu cannot be selected. When I remove and readd Russia Phonetic everything works fine until next reboot of course. Any help with that appreciated.

---


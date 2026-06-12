---
title: "K games do not run from the menu, %c from desktop entry not given"
date: 2014-05-11
forum: Desktop Environments
---

### Post by John Little on 2014-05-11
I installed Lubuntu 14.04 and found a few games in the software centre, but the games from KDE didn't work (kblocks, kmines, kpat).  Nothing happened on choosing them from the menu.  But, they worked if run from a terminal.

The problem is the %c "field code" in the "exec key" of the desktop entry is not populated.  F.ex. kpat's exec key is 
```
kpat -caption %c
```

so kpat says kpat: '<caption>' missing and does not run.  %c is meant to come from the desktop entry file Name key for the user's language, so if your language is, say, Walloon, there is a Name[wa]=KPacyince key so the %c should be  substituted with "KPacyince".  The menu system is picking this up.  I thought maybe the slightly confused nature of my language preference (en_NZ:en_AU:en_GB:en) might be causing trouble, but simplifying to just en English didn't help.  Anyway, if the language isn't found then the plain Name of the desktop entry should be used.

Simple workarounds are to edit the desktop entry exec key to remove the "-caption %c", or run the games from a terminal.  Installing KDE games in Lubuntu pulls down lots of KDE libraries, so maybe not a good idea, but if the software centre offers them they should work.

Regards, John Little

---


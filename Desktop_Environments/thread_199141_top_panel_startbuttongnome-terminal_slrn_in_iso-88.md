---
title: "top panel startbutton:gnome-terminal slrn in iso-8859-15 locale"
date: 2006-06-18
forum: Desktop Environments
---

### Post by SpeedTriple on 2006-06-18
I want to have a starterbutton in the top panel which runs gnome-terminal which runs slrn. And I need locale set to iso-8859-15 to read german language newsgroups with german umlauts properly displayed. Following manual way does the trick:

starting gnome-terminal
in gnome-terminal menubar setting encoding to iso-8859-15 (after adding a proper entry) and then entering
```
export LANG=de_DE.iso-8850-15 slrn
``` into the terminalwindow. Voilá, I got my slrn with proper umlauts! :)

So far, so boring. I found some stuff about profiles for gnome-terminal, but I found no way to set or save said encoding. How do I get that starter button with my wished settings?

---


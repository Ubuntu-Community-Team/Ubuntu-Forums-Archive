---
title: "Removing white boxes."
date: 2006-06-26
forum: Desktop Environments
---

### Post by Village Idiot on 2006-06-26
Hey Folks!...Iwas wondering if its possible to remove the annoying white boxes with the descriptions in them? You know, the ones you see when you hover your mouse over something. I'm using Gnome. I can't seem to find out how this is done.](*,)  Thank you for any help!

---

### Post by gerbman on 2006-06-28
[QUOTE=Village Idiot]Hey Folks!...Iwas wondering if its possible to remove the annoying white boxes with the descriptions in them? You know, the ones you see when you hover your mouse over something. I'm using Gnome. I can't seem to find out how this is done.](*,)  Thank you for any help![/QUOTE]Launch the configuration editor with```
gconf-editor
```Go to apps->panel->global and uncheck "tooltips_enabled".

---


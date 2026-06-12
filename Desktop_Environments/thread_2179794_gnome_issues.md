---
title: "gnome issues"
date: 2013-10-09
forum: Desktop Environments
---

### Post by ac1d2 on 2013-10-09
[ATTACH=CONFIG]246849[/ATTACH]


A picture is worth a thousand words.

I don't seem to have a directory for:
/org/gnome/gnome-panel/layout/


Our even a /org directory[SUB][/SUB]

---

### Post by Frogs Hair on 2013-10-10
Some more information may help . What version of Gnome and Ubuntu ? Is it the Gnome Shell ?

---

### Post by steeldriver on 2013-10-10
If you're asking about what I *think* you're asking about, then the answer is that they are not directories - they're schema paths in the dconf database. You should be able to list the values using

```
gsettings list-recursively org.gnome.gnome-panel
```

or (if dconf is installed)

```
dconf dump /org/gnome/gnome-panel/
```

But I agree - more info if you want a better answer

---


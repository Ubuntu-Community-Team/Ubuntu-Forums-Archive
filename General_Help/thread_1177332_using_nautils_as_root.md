---
title: "using nautils as root"
date: 2009-06-03
forum: General Help
---

### Post by feistybee on 2009-06-03
dear fellas,

this seems basic question. please help.

I want to copy some wallpapers to /usr/share/backgrounds. But I am unable to copy in nautils. Paste option is disabled.

I can do only by ```
sudo cp *.* /usr/share/backgrounds
```

Everytime opening the shell and typing command is annoying. Is there anyway I can be a root user in nautils?

---

### Post by Yellow Pasque on 2009-06-03
```
gksudo nautilus
```
Just be careful...

---

### Post by nikgare on 2009-06-03
```
sudo aptitude install nautilus-gksu
```

"The gksu extension for nautilus allows you to open files with
administration privileges using the context menu when browsing your
files with nautilus."

---

### Post by feistybee on 2009-06-04
gr8!!!. Thanks a lot.

---


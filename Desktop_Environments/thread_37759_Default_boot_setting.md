---
title: "Default boot setting?"
date: 2005-05-28
forum: Desktop Environments
---

### Post by Curlydave on 2005-05-28
Currently the default boot setting is Linux, but I want to switch it to Windows. Is there a way to change it? I'm thinking menu.list somehow, but I'm not sure exactly. Thanks!

---

### Post by Xian on 2005-05-28
[QUOTE=Curlydave]Currently the default boot setting is Linux, but I want to switch it to Windows. Is there a way to change it? I'm thinking menu.list somehow, but I'm not sure exactly. Thanks![/QUOTE]
This section in menu.lst corresponds the default system which is booted:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0
```

Zero (0) means the first entry is the default.
Change this number or move your desired OS to the first position.

Or you can add the 'savedefault' to the grub command.

---

### Post by Curlydave on 2005-05-28
That worked; Thanks!

---


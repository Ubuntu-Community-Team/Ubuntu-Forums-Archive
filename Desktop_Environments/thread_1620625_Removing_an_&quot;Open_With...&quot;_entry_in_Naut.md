---
title: "Removing an &quot;Open With...&quot; entry in Nautilus"
date: 2010-11-13
forum: Desktop Environments
---

### Post by wiznillyp on 2010-11-13
Hello all,

Does anyone know how to **remove** an "Open With" Entry in the right click menu in Nautilus?  I accidentally created an entry for all "folder" type of files for "Code::Blocks", so every time I right click a folder, I get an "Open With Code::Blocks IDE" option.

It is embarrassing! ](*,)

Also, if I posted this in the wrong category, can you please move it elsewhere?

Thanks.

---

### Post by wiznillyp on 2010-11-17
Solved my own problem:

Edited mimeapps.list entry in: ~/.local/share/applications

Removed Codeblocks reference from the following line:

```
inode/directory=userapp-nautilus-VOY0LV.desktop;codeblocks.desktop;
```

---


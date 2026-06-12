---
title: "Backup of Evolution"
date: 2006-06-05
forum: Desktop Environments
---

### Post by lean on 2006-06-05
Hey,
I have installed a freshly Ubuntu 6.06 LTS system. I now want to copy only nececarrely files from my home directory.
So my question is what files should I copy to get evolution to function properly?
I have copied .evolution and .gconf/apps/evolution, but when I start Evolution it still comes with the first time dialog, and even though my mail is present my mail accounts is not installed.

---

### Post by Rondonjin on 2006-06-05
[QUOTE=lean]Hey,
I have installed a freshly Ubuntu 6.06 LTS system. I now want to copy only nececarrely files from my home directory.
So my question is what files should I copy to get evolution to function properly?
I have copied .evolution and .gconf/apps/evolution, but when I start Evolution it still comes with the first time dialog, and even though my mail is present my mail accounts is not installed.[/QUOTE]

~/.gnome2_private/Evolution

Wayne

---

### Post by lean on 2006-06-05
I had already done that, sorry for not mentioning it.
But it is not enough. I have created a bogus account, and evolution now start without the first time dialog. If I try to delete .gconf/apps/evolution, .evolution and .gnome2_private it still goes directly into evolution. There must be some other places that is needed.

/me keeps looking...

---

### Post by ahh_dee on 2006-06-13
i just reinstalled my drapper and replaced my old evolution files.  what i did was 
```
gconftool2 --shutdown
evolution --force-shutdown
```

and then placed the files back into 

.evolution
.gconf/apps/evolution
.gnome2_private/Evolution

hope it works

---


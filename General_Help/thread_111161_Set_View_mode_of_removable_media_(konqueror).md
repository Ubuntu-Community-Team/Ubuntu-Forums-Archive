---
title: "Set View mode of removable media (konqueror)?"
date: 2006-01-01
forum: General Help
---

### Post by Mguel on 2006-01-01
I have set the default profiles of konqueror (file manager, web, etc) to use the "Tree view".

Every time I use a pen drive, whether with the auto open, or if I open it from the desktop, it opens it with the "Icon view". And even worst, after setting to Tree mode, every time I move to a folder inside the pendrive I get again the Icon view.

I have even created a new profile "removable" (with tree mode) and set ivman to use that profile:
```
<ivm:Option name="exec" value="MOUNT=$hal.block.device$; kfmclient openProfile removable media:/${MOUNT#/*/}" />
``` But it stills open it as "Icon view".

Any suggestions?

Thanks,
Mguel

PS: a work around would be use a .directory file. I have read that in the .directory file you can set the view mode, although I haven't been able to find info on how to do it. And the draw back is that it's just a workaround, and would work with my pendrive, and every time I insert another pendrive I'll have the same problem again.

---


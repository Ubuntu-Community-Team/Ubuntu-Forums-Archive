---
title: "Deleted Items Folder?"
date: 2008-05-12
forum: Desktop Environments
---

### Post by gquant on 2008-05-12
Hello,

I did a fresh install of Hardy and after a few days when all went almost perfectly, today when I logged in I realised the deleted items folder had disappeared from the panel.  I tried to add it again but to no avail, it just doesn't add it.  Furthermore there is no ~/.Trash folder.  When I delete something it turns up in ~/.local/share/Trash/files. I am probably missing something but what?

Any ideas of how I should bring things back to normal?

Thanks for any suggestions

g

---

### Post by unutbu on 2008-05-12
If you open a terminal and type
```
mkdir --mode 700 ~/.Trash
```
and then try to add Trash to your gnome panel, does that work?

---

### Post by Awalton on 2008-05-15
> **gquant said:**
> Hello,

I did a fresh install of Hardy and after a few days when all went almost perfectly, today when I logged in I realised the deleted items folder had disappeared from the panel.  I tried to add it again but to no avail, it just doesn't add it.  Furthermore there is no ~/.Trash folder.  When I delete something it turns up in ~/.local/share/Trash/files. I am probably missing something but what?

Any ideas of how I should bring things back to normal?

Thanks for any suggestions

g

Right click on the panel, select "Add to Panel...", scroll down to "Trash", and add it to the panel.

And ~/.local/share/Trash/(files,info) is the new Trash location, we're following the FreeDesktop.org Trash Specification now. Doing so will enable us to support restore-from-trash in the future, which is the intent in this change. ~/.Trash/ is now deprecated and will be removed from all GNOME components in the upcoming months.

Hope that Helps, 
-A.Walton

---


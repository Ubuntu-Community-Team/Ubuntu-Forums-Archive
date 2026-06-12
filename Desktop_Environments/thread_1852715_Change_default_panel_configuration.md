---
title: "Change default panel configuration"
date: 2011-09-30
forum: Desktop Environments
---

### Post by GlasGhost on 2011-09-30
So I tried to set the default settings with **[this]("http://ubuntuforums.org/showpost.php?p=5941192&postcount=3")**.
```
gconftool-2 --dump /apps/panel > default_settings.xml
sudo cp ./default_settings.xml /etc/gconf/schemas/panel-default-setup.entries
```

The following works. It resets the panels to the default setttings.
```
#!/bin/bash
gconftool-2 --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
However the default settings are not the new ones I made in the 1st snippet. What am I doing wrong?

---

### Post by GlasGhost on 2011-10-01
*bump*

---

### Post by Frogs Hair on 2011-10-01
It could be because the method is from a 3 year thread and it is not stated what version of Ubuntu or Gnome is being used .

---

### Post by GlasGhost on 2011-10-01
> **Frogs Hair said:**
> I could be because the method is from a 3 year thread and it is not stated what version of Ubuntu or Gnome is being used .
you could what?

also its stated that I am using gnome, but to be more specific I am using gnome 2.32.1

I am using Lucid Lynx.

---

### Post by Frogs Hair on 2011-10-01
Excuse me . I meant It could be . I was referring  to the link , it  is from before Lucid was released  , so the author could have been using Gnome 2 and not Gnome 2.32 .

---

### Post by GlasGhost on 2011-10-05
Perhaps I should just post this in the gnome forumns/mailing list.

I just thought some1 from the ubuntu community might be of help.

---


---
title: "dconf-editor does't save"
date: 2011-05-17
forum: Desktop Environments
---

### Post by inadaze on 2011-05-17
Hey,
I am trying to add some applications to the unity launcher but whenever I edit the launcher properties in dconf-editor, closing the application doesn't save the settings (when I reopen the changes are not persisted).  I am running 11.04 and most editing technics that I see are for using unity in ubuntu 10 when it wasn't a part of the OS.  Any suggestions?

---

### Post by truck87bp on 2011-05-17
Similar problem...
Tried to edit my ~/.config/Monitor.xml with Firefox open and my XML now opens as my Firefox start page.

---

### Post by mc4man on 2011-05-17
> **inadaze said:**
> Hey,
I am trying to add some applications to the unity launcher but whenever I edit the launcher properties in dconf-editor, closing the application doesn't save the settings (when I reopen the changes are not persisted).  I am running 11.04 and most editing technics that I see are for using unity in ubuntu 10 when it wasn't a part of the OS.  Any suggestions?
That's probably the worst line (favorites) to try and edit directly in dconf-editor, though certainly possible
When you highlight it is a color (default probably orange), when you edit it is white, to save to need to click out so it goes back to colored
If you make any mistakes or add in invalid path to a .desktop it won't take
Why not just add or remove directly from the launcher, either drag & drop or start app and r. click 'keep in launcher' to keep or remove an existing

You can also use gsettings command to set, but again the list can be a very long line, hardly worth the hassle

---


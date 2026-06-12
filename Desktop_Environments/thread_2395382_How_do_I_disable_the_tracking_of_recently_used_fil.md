---
title: "How do I disable the tracking of recently used files?"
date: 2018-07-01
forum: Desktop Environments
---

### Post by raphaell2 on 2018-07-01
Hi I'm using Xubuntu 18.04. How can I keep my pc from tracking my recently used files? Partly that might be specific for each application, but sometimes applications seem to show me lists of *all* files *any* application has used recently. How can I disable that?

---

### Post by #&amp;thj^% on 2018-07-01
There is a hidden file ~/.config/gtk-2.0/gtkfilechooser.ini. It should look like:
```
[Filechooser settings]
LocationMode=path-bar
ShowHidden=false
ShowSizeColumn=true
GeometryX=377
GeometryY=132
GeometryWidth=612
GeometryHeight=528
SortColumn=name
SortOrder=ascending
StartupMode=recent
```
Where I changed "StartupMode=recent" to "StartupMode=cwd"
And add the line:
```
DefaultFolder=cwd
```
**EDIT:** Replace cwd with "last" if you prefer to start with last selected folder instead.
I **think** this only works on GTK 2 applications like mousepad etc etc. 

This seems to work for GTK3:
To disable the recent files list, add the following to ~/.config/gtk-3.0/settings.ini 
```

[Settings]
gtk-recent-files-enabled=0
```

---

### Post by raphaell2 on 2018-07-01
> **1fallen said:**
> There is a hidden file ~/.config/gtk-2.0/gtkfilechooser.ini. It should look like:
```
[Filechooser settings]
LocationMode=path-bar
ShowHidden=false
ShowSizeColumn=true
GeometryX=377
GeometryY=132
GeometryWidth=612
GeometryHeight=528
SortColumn=name
SortOrder=ascending
StartupMode=recent
```
Where I changed "StartupMode=recent" to "StartupMode=cwd"
And add the line:
```
DefaultFolder=cwd
```
I think this only works on GTK 2 applications like mousepad etc etc. 


Thank you very much! I've done that now.

> 
This seems to work for GTK3:
To disable the recent files list, add the following to ~/.config/gtk-3.0/settings.ini 
```

[Settings]
gtk-recent-files-enabled=0
```

There is no setttings.ini file in my .config/gtf-3.0/ folder. The only file in that folder is "bookmarks". Should I create a settings.ini file?

---

### Post by #&amp;thj^% on 2018-07-01
> **raphaell2 said:**
> Thank you very much! I've done that now.



There is no setttings.ini file in my .config/gtf-3.0/ folder. The only file in that folder is "bookmarks". Should I create a settings.ini file?

Yes create it. :) "settings.ini "
I just to verify that you have a typeo "gtf-3.0" should be "gtk-3.0" just to be clear.;)

---

### Post by raphaell2 on 2018-07-01
> **1fallen said:**
> Yes create it. :) "settings.ini "


Thank you, that worked!

> I just to verify that you have a typeo "gtf-3.0" should be "gtk-3.0" just to be clear.;)

Oops.

Mods, can we mark this thread as solved now?

---

### Post by #&amp;thj^% on 2018-07-01
> **raphaell2 said:**
> 

Mods, can we mark this thread as solved now?

Glad that worked :)
You can mark it Solved via your first post Under "Thread Tools" Solved.

---


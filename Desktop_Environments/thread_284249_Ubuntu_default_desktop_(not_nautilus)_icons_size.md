---
title: "Ubuntu default desktop (not nautilus) icons size"
date: 2006-10-25
forum: Desktop Environments
---

### Post by bmkrein on 2006-10-25
Hi,
Can anybody tell, how to change default desktop icon size for all users in ubuntu (gnome). They are probably with 24x24 px.  How to change this in system-wide?

Sincerely, Bmkrein

---

### Post by dolphinsonar on 2006-11-23
I would also like to know.

---

### Post by bodycoach2 on 2006-12-09
I would like to learn this, too. I like having icons of things I'm working on, or using on the desktop, but the default size is SO big. 

How do you change the default size of the icons.

> **bmkrein said:**
> Hi,
Can anybody tell, how to change default desktop icon size for all users in ubuntu (gnome). They are probably with 24x24 px.  How to change this in system-wide?

Sincerely, Bmkrein

---

### Post by SlCKB0Y on 2006-12-10
After searching on google for about 5 minutes, I found a couple of different solutions

[http://gnomesupport.org/forums/viewtopic.php?t=1975&sid=61e3faf607cbe77c5cfb2074c5e423f2](http://gnomesupport.org/forums/viewtopic.php?t=1975&sid=61e3faf607cbe77c5cfb2074c5e423f2)
[http://gnomesupport.org/forums/viewtopic.php?t=7156&sid=196b1541f7dd91b0ed99c28c1aab8931](http://gnomesupport.org/forums/viewtopic.php?t=7156&sid=196b1541f7dd91b0ed99c28c1aab8931)

---

### Post by moeFinley on 2007-01-10
I found the best solution was [this]("http://gnomesupport.org/forums/viewtopic.php?t=10961")

> if not already there, create a .gtkrc-2.0 file in your home directory, put this in it 
```
gtk-icon-sizes = "panel-menu=16,16:panel=16,16:gtk-menu=16,16:gtk-large-toolbar=16,16:gtk-button=16,16"
```

Make sure use create a new file as above and don't use the .gtkrc-1.2-gnome2 file that is also in your directory.

---

### Post by Dilox on 2007-01-22
Another forum person suggested:

Home Folder>Edit>Preferences>Views>Default zoom level change that to 75% its a pretty good size.

Dylan

---


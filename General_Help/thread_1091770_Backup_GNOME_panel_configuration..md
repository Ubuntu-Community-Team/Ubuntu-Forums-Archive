---
title: "Backup GNOME panel configuration."
date: 2009-03-09
forum: General Help
---

### Post by cometa2k7 on 2009-03-09
Basically, I would like to know which files I would need to backup if I wanted to change the GNOME panel, but be able to revert back at a later date.

I want to try a different set-up, similar to what I use on DreamLinux with XFCE, but it's quite different to my set-up for GNOME at the moment.

---

### Post by cometa2k7 on 2009-03-10
Bump

---

### Post by leaphion on 2009-05-03
Would this be close to what you're looking for?

[http://ubuntuforums.org/showthread.php?t=66040](http://ubuntuforums.org/showthread.php?t=66040)

---

### Post by Legace on 2009-05-03
You could backup
```
/home/YOURNAME/.gconf/apps/panel
```

as the panel folder contains the settings of the panel.
And then restore when needed.

Requires logoff and then logon to for changes to appear.

---

### Post by Ghuul on 2010-01-01
You can use gconftool.

Eg. use "gconftool --dump /apps/panel > backup.xml" to save your settings and to restore using "gconftool --load backup.xml".

---


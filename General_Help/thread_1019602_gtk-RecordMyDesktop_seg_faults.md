---
title: "gtk-RecordMyDesktop seg faults"
date: 2008-12-23
forum: General Help
---

### Post by obsrv on 2008-12-23
I want to use gtk-recordMyDesktop to record my brand new Ubuntu 9.04 A2 Eye-Candyness, but after stopping record it segafaults. Output:

```
obsrv@PIRATE:~$ gtk-recordMyDesktop 
/var/lib/python-support/python2.5/recordMyDesktop/rmdPrefsWidget.py:246: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.channelsSpinButton= gtk.SpinButton(self.channelsAdjustment, climb_rate=0.5, digits=0)
Segmentation fault
obsrv@PIRATE:~$ gtk-recordMyDesktop 
Segmentation fault
obsrv@PIRATE:~$ 


```

---

### Post by Usufruct on 2008-12-23
Are you using the newest version of gtk-recordMyDesktop?

---

### Post by obsrv on 2008-12-23
Yes I am usign the lastes jaunty version. Maybe it caused by Compiz-Fusion or mplayer? if mplayer is used for encoding.

---

### Post by obsrv on 2008-12-24
Bump :)

---

### Post by obsrv on 2008-12-26
Is there any alternative to GTK-RecordMyDesktop?

---


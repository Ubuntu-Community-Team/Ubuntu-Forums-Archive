---
title: "Terminal transparent background problem"
date: 2009-04-03
forum: Desktop Environments
---

### Post by IsmailBhai on 2009-04-03
In 8.10, when I had the terminal background as transparent, the icons on the desktop would also show up.  If a windows was open, it would also show through the transparency, but now after upgrading to Jaunty, only the background shows up.  Any ideas?

---

### Post by zhocchao on 2009-04-03
is /apps/metacity/general/compositing_manager enabled (gconf)?

---

### Post by blazemore on 2009-04-03
Either enable Metacity compositing (as zhocchao said)
Or use another compositing window manager, like Compiz.

---

### Post by IsmailBhai on 2009-04-03
how do i switch a composting window manager? like from Metacity to Compiz?

---

### Post by UbuntuNerd on 2009-04-03
go to synaptic package manager and search and install the package "Fusion icon" which is a tray icon that let you switch between compiz or metacity

---

### Post by IsmailBhai on 2009-04-03
thanks guys, the problems was that it works only in compiz and not metacity.  I enabled compiz by going to system-> Prefs->appearance-> visual effects -> normal

---

### Post by blazemore on 2009-04-06
Yes, true transparency only works with a compositing Window Manager.

---


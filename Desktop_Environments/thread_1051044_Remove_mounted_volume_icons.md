---
title: "Remove mounted volume icons"
date: 2009-01-26
forum: Desktop Environments
---

### Post by jon.mithe on 2009-01-26
Hi,

Does anyone know of a way of preventing icons from appearing on the desktop when network drives etc mount?  I.e. when something like that mounts you get an annoying shortcut to is on the desktop that you can not delete.  I'm runnning a standard + uptodate version of 8.10.

Thanks for any help,
Jon

---

### Post by gettinoriginal on 2009-01-26
Press "alt+f2" enter "gconf-editor".

Navigate to "apps -> naulilus -> desktop" and make sure the last box is untagged.

That way no removable media will appear on the desktop.

---

### Post by Tim Sharitt on 2009-01-26
Hit Alt-F2 and enter gconf-editor. In the left pane expand apps, scroll down and expand nautilus and click on desktop. There is a list of options in the right pane. Un-check volumes to keep volumes from apearing on the desktop.

---

### Post by jon.mithe on 2009-01-26
Thats worked a treat, thank you both for your help! :)

---


---
title: "Where does ubuntu store the keyboard shortcuts?"
date: 2009-08-04
forum: Desktop Environments
---

### Post by luajunyi on 2009-08-04
Thanks.

---

### Post by prshah on 2009-08-04
> **luajunyi said:**
> Thanks.

Usually accessible through System-Preferences-Keyboard shortcuts; or in ~/.gnome2/accels/ directory.

---

### Post by kpkeerthi on 2009-08-04
If you are using Compiz (Desktop Effects), check under CCSM -> General -> Commands. You can install ccsm using Synaptic. Package name is compizconfig-settings-manager

---

### Post by Andreas1 on 2009-08-04
i also found some in

.gconf/apps/metacity/global_keybindings/%gconf.xml
.gconf/apps/metacity/window_keybindings/%gconf.xml

if you want to change them i would use gconf-editor or gconftool

---


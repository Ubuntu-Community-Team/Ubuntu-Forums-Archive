---
title: "CHange theme without GUI"
date: 2005-11-06
forum: Desktop Environments
---

### Post by christooss on 2005-11-06
Can I change my theme with editing one of many config files?

If I refrase this. Where does gnome-theme-manager writes to?

---

### Post by ow50 on 2005-11-06
[QUOTE=christooss]Can I change my theme with editing one of many config files?

If I refrase this. Where does gnome-theme-manager writes to?[/QUOTE]
The following gconf keys:
/desktop/gnome/interface/gtk_theme
/desktop/gnome/interface/icon_theme
/apps/metacity/general/theme

Use gconftool-2 to change them at the command line.

---

### Post by christooss on 2005-11-06
Thanks. I found gconf.xmls which I have to edit. Thanks again

---


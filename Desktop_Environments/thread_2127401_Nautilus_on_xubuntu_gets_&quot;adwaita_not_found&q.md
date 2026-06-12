---
title: "Nautilus on xubuntu gets &quot;adwaita not found&quot;"
date: 2013-03-19
forum: Desktop Environments
---

### Post by Ralph L on 2013-03-19
I installed nautilus on xubuntu 12.04.2, but when I launch it from Terminal, it gets the following error message.  Is there a way to install adwaita theme and make this go away?

```
ralph@pres:~$ nautilus

(nautilus:4667): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2:16: Theming engine 'adwaita' not found

(nautilus:4667): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:909:16: Theming engine 'adwaita' not found
ralph@pres:~$ !!
```

---

### Post by Krytarik on 2013-03-20
The Adwaita theme engine (as well as the equally named theme) is included in the package "gnome-themes-standard", so e.g.:
```
sudo apt-get install gnome-themes-standard
```
Regards.

---

### Post by Ralph L on 2013-03-22
Krytarik

That worked.  Thank you very much.
Ralph

---


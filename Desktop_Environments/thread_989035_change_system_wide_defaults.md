---
title: "change system wide defaults"
date: 2008-11-21
forum: Desktop Environments
---

### Post by krisek on 2008-11-21
I would like to change the system wide default font, theme and background settings.

The goal is to have the same default for all users of the box without changing anything in their own profile. (Or in /etc/skel.)

Subject of customization:
[LIST]
[*]Gnome fonts
[*]Qt3, Qt4 fonts
[*]Theme, background (ok here I can replace Human in /usr/share/themes, but I guess at the next system upgrade this config will be lost)
[/LIST]

Any idea?

---

### Post by jrib on 2008-11-21
Take a look at [http://library.gnome.org/admin/](http://library.gnome.org/admin/) .  For the settings controlled by gconf at least, you can just set gconf defaults ([http://library.gnome.org/admin/system-admin-guide/stable/gconf-24.html.en](http://library.gnome.org/admin/system-admin-guide/stable/gconf-24.html.en)) using the procedure in [http://library.gnome.org/admin/system-admin-guide/stable/gconf-7.html.en](http://library.gnome.org/admin/system-admin-guide/stable/gconf-7.html.en)

---

### Post by krisek on 2008-11-21
Many thanks, it works like charm. I realized that it is a possibility as well to start gconf-editor as root, in this case a context menu of keys/values is updated with two items called 'Set as default' and 'Set as locked'.

With qt the situation is not that simple, I found that for qt3 I need to update /etc/qt3/qtrc, and for qt4 I need to create /etc/xdg/Trolltech.conf (But this is still a kind of /etc/skel solution which I would like to avoid.)

---


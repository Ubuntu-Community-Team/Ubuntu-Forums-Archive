---
title: "Kiba-dock problem"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by Fidelity on 2007-05-03
When I try to start kiba dock, I get this

> $ kiba-dock

(kiba-dock:6805): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion `icon_i         nfo != NULL' failed

(kiba-dock:6805): GLib-CRITICAL **: g_str_has_suffix: assertion `str != NULL' fa         iled

(kiba-dock:6805): Gtk-CRITICAL **: gtk_icon_theme_lookup_icon: assertion `icon_n         ame != NULL' failed
Segmentation fault (core dumped)


What could the problem be? I installed via the "wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | su
do apt-key add -
" method

---

### Post by scanez on 2007-05-03
Run gset-kiba first (which will also give errors), then run kiba-dock.

---


---
title: "Some programs look ugly"
date: 2012-02-02
forum: Desktop Environments
---

### Post by Nixot on 2012-02-02
I've noticed this for quite some while now. I don't understand why it is happening either - doesn't Xfce use GTK to display widgets? Why, then, do some GNOME programs like file-roller have these ugly Windows-98-esque things on them? The link below shows what I'm talking about (picture 1 is how things are supposed to look, pictures 2 and 3 are examples of the ugliness mentioned above).

[http://imgur.com/a/CNH6q](http://imgur.com/a/CNH6q)

installing qtcurve, or any qt-related GTK software did not work (qgtkstyle, gtk-qt, etc). Neither did following other posts about Xubuntu ugliness, which were about modifying ~/.gtkrc-2.0.

Any help with this would be much appreciated. thanks!

---

### Post by Sonador on 2012-02-02
Hi,  the reason is gnome3 is based on gtk3 now, but xfce 4.8 still use gtk2, one of few workarounds is to create symlink **~/.config/gtk-3.0** which refers to **/usr/share/themes/Adwaita/gtk-3.0**    

Or use theme for xfce which has gtk3 support, I don't remember which one, if any.

---

### Post by Toz on 2012-02-02
> **Sonador said:**
> Or use theme for xfce which has gtk3 support, I don't remember which one, if any.

Greybird is one. You can look for others at xfce-look.org. Search themes for keyword 'gtk3'.

---


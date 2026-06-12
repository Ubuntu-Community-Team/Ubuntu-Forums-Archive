---
title: "ubuntu gnome 12.10, mixed GTK color theme problem"
date: 2012-10-22
forum: Desktop Environments
---

### Post by cb951303 on 2012-10-22
Some applications use a dark color theme whereas others use a light color theme.

Here is a screenshot:
[http://i.imgur.com/bhuD5.jpg](http://i.imgur.com/bhuD5.jpg)

---

### Post by mpmistr on 2012-10-22
> **cb951303 said:**
> Some applications use a dark color theme whereas others use a light color theme.

Here is a screenshot:
[http://i.imgur.com/bhuD5.jpg](http://i.imgur.com/bhuD5.jpg)

Use Gnome Tweak Tool to set "Use Dark Theme".

However it appears that GTk2 applications are not affected by this. If there is a way to get GTk2 applications to use Adwaita Dark I'd love to know because it's driving me crazy!

---

### Post by cb951303 on 2012-10-22
> **mpmistr said:**
> Use Gnome Tweak Tool to set "Use Dark Theme".

However it appears that GTk2 applications are not affected by this. If there is a way to get GTk2 applications to use Adwaita Dark I'd love to know because it's driving me crazy!

silly me I didn't notice they were gtk2 applications.

---

### Post by mpmistr on 2012-10-22
Technically speaking gEdit and Nautilus should be using the Adwaita Dark theme if you have that toggle enabled as they are both native Gtk themes. For some reason by default Totem, Cheese, Image Viewer and a few other applications will use the Adwaita Dark theme no matter what.

I'm still a bit confused by this, I do think the Adwaita Dark theme does look nice though but it will only work on Gtk3 apps as I stated earlier.

---

### Post by cb951303 on 2012-10-23
on top of that, chromium still uses light theme even though dark theme is switched on from gnome-tweak tool.

kinda messy.

---


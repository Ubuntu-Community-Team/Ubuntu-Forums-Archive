---
title: "can't start gedit from terminal"
date: 2005-10-24
forum: Desktop Environments
---

### Post by davegahan on 2005-10-24
When trying to edit xorg.conf i get this error message

gedit xorg.conf

(gedit:8407): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gn ome' which is needed to make this application accessible
GTK Accessibility Module initialized

(gedit:8407): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bri dge' which is needed to make this application accessible

I do not have problems opening from applications/accessories
Whats wrong ?

---

### Post by Efwis on 2005-10-24
are you using sudo with the gedit command???

```
sudo gedit /etc/X11/xorg.conf
```

---


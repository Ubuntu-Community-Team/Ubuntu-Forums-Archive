---
title: "Xfce panel shadow"
date: 2012-06-03
forum: Desktop Environments
---

### Post by tivatranquio on 2012-06-03
How can I enable the shadow for the xfce panel?

---

### Post by 2F4U on 2012-06-03
If I am not wrong, you would have to enable the internal XFCE compositor. There is an option called "Show shadows under dock windows" which should give you that effect.

---

### Post by tivatranquio on 2012-06-03
I have checked it but the shadow still not appear

---

### Post by Jose Catre-Vandis on 2012-06-03
Do you mean for "the panel" or just all windows?

There is no shadow for the panel.

Activating the xfce compositor (Settings > Window Manager Tweaks > Compositor > Tick) will give shadows and opacity effects to windows

from command line:
```
xfconf-query --channel=xfwm4 --property=/general/use_compositing --set=true or false
```

To access panel settings (with compositor on) Right click on panel > Panel > Panel Preferences > Display & Appearance Tabs

---

### Post by tivatranquio on 2012-06-06
and if i use compiz?

---

### Post by black veils on 2012-06-06
maybe you are just wanting the panel itself to look 3D  ?   if so, here are some images (themes) you can apply to the panel:

1.  [http://gnome-look.org/content/show.php/Panel+Background+pack+7?content=151112](http://gnome-look.org/content/show.php/Panel+Background+pack+7?content=151112)

2.  [http://xfce-look.org/content/show.php/Bottom+Panel+Backgrounds+Pack?content=150311](http://xfce-look.org/content/show.php/Bottom+Panel+Backgrounds+Pack?content=150311)

---

### Post by vasa1 on 2012-06-06
> **tivatranquio said:**
> and if i use compiz?
Why use Xfce then?

---


---
title: "Qt doesn't use GTK dialogs in XFCE"
date: 2011-11-03
forum: Desktop Environments
---

### Post by fomik on 2011-11-03
I installed qt on my Xubuntu, but all qt applications don't use native gtk open/save dialogs like in Gnome. Does anyone know how to make Qt using native gtk dialogs? Qt apps are using native gtk dialogs in Gnome, so there must be such way.
Thanks in advance.

---

### Post by fomik on 2011-11-04
Attaching screenshot.

---

### Post by gsmanners on 2011-11-04
Maybe check this out: [http://forum.xfce.org/viewtopic.php?id=5605](http://forum.xfce.org/viewtopic.php?id=5605)

---

### Post by cottfcfan on 2011-11-05
I had the same problem.
You need to install libgnomeui-common & libgnomeui-0.
They're in synaptic.

---

### Post by fomik on 2011-11-07
Well...but this will install Gnome libs, which I don't want.

---

### Post by cottfcfan on 2011-11-07
Afraid its the only way.

---

### Post by kholis on 2011-12-01
> **cottfcfan said:**
> I had the same problem.
You need to install libgnomeui-common & libgnomeui-0.
They're in synaptic.

Didn't works on my laptop. I've already install the packages but Qt based apps still uses gnome icon instead of elementary icon.

Any clue?

Thanks

---

### Post by cottfcfan on 2011-12-01
The only QT apps I use are Luckybackup & keepassx.
The above 2 packages were to make the appearance, of QT apps integrate with the desktop.
The Icons are a different matter.
The Faenza icon set works with keepass but nothing ive tried changes the luckybackup icon.
I guess you'll probably need some kde based icons to do that.
You can of course find your own icon & manually change it.

---


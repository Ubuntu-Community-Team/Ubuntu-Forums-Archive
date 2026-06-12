---
title: "xorg.config is readonly"
date: 2005-12-23
forum: General Help
---

### Post by nami on 2005-12-23
Hi

When I installed a copy of ubuntu 5.10, I noticed that the resolution was too high, so from within gnome>system>preferences>screen resolution, I changed the resolution to 1024x768.  This is the default resolution of my monitor and things look much better.

However, I have noticed that the login screen is still using the high resolution!  I did a search in this forum and found that I need to change the xorg.config file.  I double click this file to open it and when I try to change the text nothing happens.  I then noticed "on the title bar of the window" that the xorg.config file was was read only?

Why is it read only and how do I open this file so I can make the change?

Appreciate any help

nami

---

### Post by Lvnielen on 2005-12-23
in a terminal:

[PHP]sudo gedit /etc/X11/xorg.conf[/PHP]

good luc

---

### Post by Manuel Siggen on 2005-12-23
Hi Nami,

I guess that's because you need to edit the file as root. Try :

```
sudo gedit /etc/X11/xorg.conf
```

Cheers,

   Manuel

---

### Post by nami on 2005-12-23
That's perfect!  Thanks

Restarting the box now to see if it's made a difference...

nami

[edit]That's much better!  Thanks again.[/edit]

---


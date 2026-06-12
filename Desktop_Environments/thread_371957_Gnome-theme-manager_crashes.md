---
title: "Gnome-theme-manager crashes"
date: 2007-02-27
forum: Desktop Environments
---

### Post by ZiTriX on 2007-02-27
When i start gnome-theme-manager it crashes almost emediately, when i run it from a terminal i get an error message:
> zitrix@sLAN:~$ gnome-theme-manager

(gnome-theme-manager:4433): Gtk-WARNING **: Theme file for MacOS-X has no name


(gnome-theme-manager:4433): Gtk-WARNING **: Theme file for MacOS-X has no directories

zitrix@sLAN:~$ 

It seems like there is a theme there that shouldn't be there, and in that case, where is the theme folder?

Or anyone know any other way to fix it?

Glad for answers :)

---

### Post by ComplexNumber on 2007-02-27
> **ZiTriX said:**
> When i start gnome-theme-manager it crashes almost emediately, when i run it from a terminal i get an error message:


It seems like there is a theme there that shouldn't be there, and in that case, where is the theme folder?

Or anyone know any other way to fix it?

Glad for answers :)
the reason why is because there is something wrong with the index.theme file. will you give me a printout of what the index.theme file says in the icon theme MacOS-X. thanks.

---

### Post by ZiTriX on 2007-02-27
Now the whole system have crasched, so I did a reinstall instead :/

---

### Post by ComplexNumber on 2007-02-27
> **ZiTriX said:**
> Now the whole system have crasched, so I did a reinstall instead :/
oh no! please don't say that. it was really easy to fix. the reason for the error is because  either the  index.theme file in the MacOS-X icons or the gtk theme didn't correspond to the standard format.

---


---
title: "gnome window list sorting order"
date: 2005-04-21
forum: Desktop Environments
---

### Post by michael_salcher on 2005-04-21
hi

does anyone know how to change the way the gnome window list (task bar) sorts the windows? it seems to do it alphabetically (at least sometimes) which is not very helpful. it should really sort them chronologically by when the time these windows have been opened.

thanks

---

### Post by globalspace on 2005-04-21
[QUOTE=michael_salcher]hi

does anyone know how to change the way the gnome window list (task bar) sorts the windows? it seems to do it alphabetically (at least sometimes) which is not very helpful. it should really sort them chronologically by when the time these windows have been opened.

thanks[/QUOTE]

type in shell :

> gconf-editor 

**Apps -> Nautilus -> Icon View -> default_sort_order -> **

change **name** with **modification_date**

gconf rulez  :razz:

---

### Post by jallen7usa on 2005-04-24
[QUOTE=globalspace]
gconf rulez  :razz:[/QUOTE]

WOW!  I've been wondering about this for so long and just assumed you couldn't change it (windows mentality).  Thank you.

---

### Post by chettyk on 2005-04-24
[QUOTE=globalspace]type in shell :

 

**Apps -> Nautilus -> Icon View -> default_sort_order -> **

change **name** with **modification_date**

gconf rulez  :razz:[/QUOTE]


Couldn't the same be achieved without using gconf-editor by opening a nautilus window, then Edit -> Preferences -> Views tab, and setting 'Arrange items:' option to 'By Modification Date'?

---

### Post by michael_salcher on 2005-04-26
i don't think changing the settings through the preferences menu of nautilus would work, because i changed the settings through the gconf editor but when i look at the preferences menu of nautilus now, its settings haven't changed although the sorting order of the gnome window list seems to have changed

---


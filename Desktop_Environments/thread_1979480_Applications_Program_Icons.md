---
title: "Applications Program Icons"
date: 2012-05-13
forum: Desktop Environments
---

### Post by Geffers on 2012-05-13
The program icons that come up when you hover over the Applications task bar menu, I assume they are just program shortcuts, where are they listed.

Geffers

---

### Post by Frogs Hair on 2012-05-13
> **Geffers said:**
> The program icons that come up when you hover over the Applications task bar menu, I assume they are just program shortcuts, where are they listed.

Geffers

If you select the top icon it will open dash and the categories are listed there. See the link for user tips. 

[http://fridge.ubuntu.com/2011/04/21/the-power-user’s-guide-to-unity/](http://fridge.ubuntu.com/2011/04/21/the-power-user’s-guide-to-unity/)

---

### Post by Krytarik on 2012-05-14
> **Geffers said:**
> The program icons that come up when you hover over the Applications task bar menu, I assume they are just program shortcuts, where are they listed.
The corresponding .desktop files are under "/usr/share/applications" (system-wide) and "~/.local/share/applications" (user-specific, custom).

Regards.

---

### Post by Geffers on 2012-05-14
> **Krytarik said:**
> The corresponding .desktop files are under "/usr/share/applications" (system-wide) and "~/.local/share/applications" (user-specific, custom).

Regards.

Thank you, they all appear to be listed in the  /usr/share/applications directory but how do the applications then appear in sub sections from the Task Bar.

Geffers

---

### Post by Krytarik on 2012-05-15
> **Geffers said:**
> Thank you, they all appear to be listed in the  /usr/share/applications directory but how do the applications then appear in sub sections from the Task Bar.
That's specified by their respective "Categories" key. For further reading:

[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

---


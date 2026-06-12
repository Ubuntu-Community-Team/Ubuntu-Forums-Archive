---
title: "How Can I lock the desktop icons from being deleted?"
date: 2008-06-07
forum: Desktop Environments
---

### Post by mister_p_1998 on 2008-06-07
Jus built my son a nice Hardy machine, whch runs a treat with all the educational s/ware on it. Trouble is, he keeps deleting and moving the icons on the desktop, and dragging them onto the taskbar. I want to lock them so he cant do this. Ive tried making him a lower access user, doing Sudo Nautilus and making the icons read-only to him, but he can still delete them. How do I fix this?

Steve

---

### Post by abhiroopb on 2008-06-07
[http://library.gnome.org/admin/deployment-guide/](http://library.gnome.org/admin/deployment-guide/)

---

### Post by mister_p_1998 on 2008-06-07
> **abhiroopb said:**
> [http://library.gnome.org/admin/deployment-guide/](http://library.gnome.org/admin/deployment-guide/)

Nope, didnt work...
I enabled lockdown on the gnome panel, and the user can still delete Icons.

---

### Post by bazzer on 2008-06-09
Well, you could log in as a superuser and change permissions for the items in the Desktop folder that end in '.desktop' to read only? Also, the desktop icons are placed in position with a file in ~/.nautilus/metafiles/
It's an XML file, so I guess if you set it to read only, it shouldn't change - meaning anything added to the desktop will 'fall off' when you log off. Your mileage may vary though.

---


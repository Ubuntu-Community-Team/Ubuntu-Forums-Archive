---
title: "NixNote location change in XFCE app menu."
date: 2011-09-07
forum: Desktop Environments
---

### Post by casbahdk on 2011-09-07
I just discovered and installed NixNote on Xubuntu 11.04. The app works great, but there is a little hiccup regarding it's location in the XFCE applications menu. It is listed under "Internet", but in my opinion it doesn't matter what environment it works in as we all work both on our desktop and in "the cloud" at the same time. I would like to edit the .desktop file so that it is placed under either the "office" or "accessories" category in the applications menu. Unfortunately, I don't know where those files are located and it isn't possible to just right click the item to edit it's properties as in GNOME. Anyone have an idea about this?

---

### Post by raja.genupula on 2011-09-07
[http://library.gnome.org/admin/system-admin-guide/2.32/menustructure-2.html.en](http://library.gnome.org/admin/system-admin-guide/2.32/menustructure-2.html.en)


this link gonna help you

---

### Post by casbahdk on 2011-09-07
> **raja.genupula said:**
> [http://library.gnome.org/admin/system-admin-guide/2.32/menustructure-2.html.en](http://library.gnome.org/admin/system-admin-guide/2.32/menustructure-2.html.en)


this link gonna help you
Cheers. I haven't been able to find any file in .config or in /etc/xdg that lists an entry with the parameters for "nevernote" or "nixnote". That is at least where I understand that it should reside, according to the information provided at the URL.

---

### Post by Toz on 2011-09-07
I believe the file you need to edit is **/usr/share/applications/nixnote.desktop**. 

Change "Categories=Network;" to read either:

**Categories=Office;** or **Categories=Utility;**

---

### Post by casbahdk on 2011-09-08
> **Toz said:**
> I believe the file you need to edit is **/usr/share/applications/nixnote.desktop**. 

Change "Categories=Network;" to read either:

**Categories=Office;** or **Categories=Utility;**

Many thanks Toz, that was exactly what I needed.

---

### Post by Toz on 2011-09-08
Glad to head. Can you please mark the thread as Solved from the Thread Tools link above?

---


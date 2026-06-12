---
title: "Applications menu in wrong language"
date: 2008-07-14
forum: Desktop Environments
---

### Post by jis on 2008-07-14
I switched back to English in login and now applications seem to be in English, but not Applications menu of Xfce. How can you fix that?

---

### Post by jis on 2008-07-14
Later the menu became English, too. I don't know what caused it to, though.

---

### Post by jis on 2008-07-14
Maybe the menus were updated because I installed a new application.

---

### Post by mali2297 on 2008-07-14
> **jis said:**
> Maybe the menus were updated because I installed a new application.

Yes, that seems reasonable since the menu is auto-generated. 

It is stored in an xml file in the directory *~/.cache/xfce4/desktop/*. An alternative might have been to force a regeneration by deleting that file.

---


---
title: "octal permissions in Nautilus"
date: 2008-05-29
forum: Desktop Environments
---

### Post by akahige on 2008-05-29
Is there a way to CHMOD octal permissions in Nautilus?

---

### Post by tamoneya on 2008-05-29
right click the file then go properties -> permissions

---

### Post by akahige on 2008-05-30
I'm not seeing **octal** permissions at all.

---

### Post by tamoneya on 2008-05-30
they are the same thing they just dont display in octal.  It will set the octal for you accordingly.

---

### Post by akahige on 2008-05-30
I'm well aware of how permissions work.

How hard is it to understand that the question I'm asking is whether or not there's a way to -- or a hack so -- you can change permissions in Nautilus using octal values?

---

### Post by fsando on 2008-10-26
> **akahige said:**
> I'm well aware of how permissions work.

How hard is it to understand that the question I'm asking is whether or not there's a way to -- or a hack so -- you can change permissions in Nautilus using octal values?

Please don't take your frustration out on those who try to help you.

I don't believe Nautilus has an octal interface as such but there is something that may do:

In the console run
```
gconf-editor
```
under 'apps/nautilus/preferences' tick the item 'show_advanced_permissions' (if it doesn't exists add it)

This will give you a detailed view of permissions

---


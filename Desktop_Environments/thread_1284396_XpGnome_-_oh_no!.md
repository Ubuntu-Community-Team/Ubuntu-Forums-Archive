---
title: "XpGnome - oh no!"
date: 2009-10-06
forum: Desktop Environments
---

### Post by mariuszp on 2009-10-06
Man, I'm bored of the XpGnome theme. So what? I could just change my theme. But there is actually something that I desperatly need to do but don't know how to - get rid of My Computer and other Window XP icons from my desktop. I can't cut, copy, or put them in trash or anything. So what do I have to do?

EDIT: I'm using GNOME desktop.

---

### Post by mister_p_1998 on 2009-10-08
try gconf-editor

---

### Post by mcduck on 2009-10-08
> **mariuszp said:**
> Man, I'm bored of the XpGnome theme. So what? I could just change my theme. But there is actually something that I desperatly need to do but don't know how to - get rid of My Computer and other Window XP icons from my desktop. I can't cut, copy, or put them in trash or anything. So what do I have to do?

EDIT: I'm using GNOME desktop.

Open gconf-editor (press alt-f2 and run "gconf-editor"). Browse to apps/nautilus/desktop and you'll find options for enabling/disabling different desktop icons.

---


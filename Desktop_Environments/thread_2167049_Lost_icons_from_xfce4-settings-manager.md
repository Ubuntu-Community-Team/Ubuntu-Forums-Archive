---
title: "Lost icons from xfce4-settings-manager"
date: 2013-08-12
forum: Desktop Environments
---

### Post by vinibali on 2013-08-12
hi,
while i tired to finetune the others selection from main menu, i lost the icons from the settings manager.
 now i cant restore these, its really annoying. i tried to remove xfce config files, but nothing helps
thanks

---

### Post by Buntu Bunny on 2013-08-12
Just to clarify; you don't mean icons in general, you mean icons for specific settings: display, removable drives, workspaces, etc.?

---

### Post by vinibali on 2013-08-12
yes, exactely :)

---

### Post by Bashing-om on 2013-08-12
vinibali; Hi !

Try the simpler approach first and see:
Let's clear the session cache:
 logout, ctrl+alt+f2,
 login in the text console and
Terminal code:
```

rm -rf .cache/sessions

```
then ctrl+alt+f7  
and login again.

[INDENT][INDENT]hey just try'n to help
[/INDENT][/INDENT]

---

### Post by vinibali on 2013-08-12
its not :/
but anyway, thanks!

---


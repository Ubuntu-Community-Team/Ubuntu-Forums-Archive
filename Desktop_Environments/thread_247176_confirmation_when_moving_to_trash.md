---
title: "confirmation when moving to trash"
date: 2006-08-30
forum: Desktop Environments
---

### Post by DamianABBA on 2006-08-30
Is it possible to make nautilus ask for a confirmation when moving something to trash?

---

### Post by CatKiller on 2006-08-31
I thought it did so by default. Anyway, open up the Configuration Editor (gconf-editor) and navigate to apps/nautilus/preferences and tick the confirm_trash checkbox.

---

### Post by aysiu on 2006-08-31
Nautilus > Edit > Preferences
See screenshot.

---

### Post by DamianABBA on 2006-08-31
// I thought it did so by default. Anyway, open up the Configuration Editor
// (gconf-editor) and navigate to apps/nautilus/preferences and tick the
// confirm_trash checkbox.

That was already checked, but doesn't seem to work.

---

### Post by DamianABBA on 2006-08-31
// Nautilus > Edit > Preferences
// See screenshot.

"Ask before emptying the Trash or deleting files"
That's ok, but I want a confirmation when moving something to trash.
I think when i installed ubuntu there was a confirmation box when moving something to trash, but I disabled it through gconf, and now I try to enable it, I check the checkbox, but nothing happens.

---

### Post by aysiu on 2006-08-31
If you check it off the way I have it in the screenshot, it'll prompt you before moving stuff to the trash.

---

### Post by DamianABBA on 2006-08-31
It's checked, but i get no prompt when moving to trash... if i uncheck it, the only diff I see, is that when empty trash i get no msg for confirmation. Anyway, I checked it and receive prompt when emptying trash, but not when moving something to trash. :confused:

---


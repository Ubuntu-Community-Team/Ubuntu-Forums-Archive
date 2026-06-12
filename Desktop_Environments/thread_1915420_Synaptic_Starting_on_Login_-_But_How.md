---
title: "Synaptic Starting on Login - But How?"
date: 2012-01-26
forum: Desktop Environments
---

### Post by iposner on 2012-01-26
Using Xubuntu - somehow the Synaptic application is starting after login, but I can't see it in the list of startup applications, so how else is it getting started?

---

### Post by Toz on 2012-01-26
Its in your saved sessions cache. When you logout, you have the option to "Save session for future logins". If this is checked, it will save any open applications and re-open them on the next login.

You can either close all open applications, logout and unselect the checkbox to save sessions (and make sure its unchecked when you logout to ensure that no sessions are being saved), or you can delete your ~/.cache/sessions directory to delete all saved sessions.

---

### Post by iposner on 2012-01-28
Thanks! That seems to have worked fine!

---


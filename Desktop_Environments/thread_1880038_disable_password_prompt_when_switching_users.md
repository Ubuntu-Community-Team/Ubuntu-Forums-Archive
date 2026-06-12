---
title: "disable password prompt when switching users?"
date: 2011-11-12
forum: Desktop Environments
---

### Post by matthewn on 2011-11-12
I've got 11.10 on a desktop machine with two users. Both users have "Password" set to "Not asked on login" in Users Settings. At startup, either user can log in without a password. But once both users are logged in, it takes a password to switch between users.

In previous Ubuntus, you could override this by setting /desktop/gnome/lockdown/disable_lock_screen to True in gconf-editor. That is ignored in the Gnome 3 / Unity era.

Does anyone know a way to disable the password prompt when switching between users in Oneiric?

---

### Post by matthewn on 2011-11-23
In case anyone comes across this thread, I found the solution. It's in dconf/gsettings now. So fire up dconf-editor and alter: org.gnome.desktop.lockdown.disable-lock-screen.

---


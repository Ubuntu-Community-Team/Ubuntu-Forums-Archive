---
title: "[gtk] mono apps don't work after installing KDE app"
date: 2009-05-03
forum: General Help
---

### Post by alex_sv on 2009-05-03
I've installed Umbrello on my ubuntu which is KDE app.
Looks like installation process of KDE apps brokes bindings to the mono assemblies (at least MONO_PATH is no longer exists after installing any KDE app) what brokes all the mono apps (f-spot, tomboy)...

Is it a known issue and I shouldn't install KDE apps if I use gnome?
Are there any known issues with co-existence of KDE and Gnome on the single computer?

---

### Post by directhex on 2009-05-03
There should be no such issues, and MONO_PATH should not be set by default.

What does "mono --version" report?

---


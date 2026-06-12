---
title: "Ubuntu 16.04 Nautilus windows close themselves"
date: 2016-09-20
forum: Desktop Environments
---

### Post by cpsj on 2016-09-20
If I open a Nautilus window (to open a file, say) and then do something else the Nautilus window closes itself and I have to start again :(. This has only happened since I upgraded from 14.04

---

### Post by RamonB on 2016-09-20
The same problem is occurring to me. I installed 16.04 months ago but the problem appeared just now.

***UPDATE***: the problem is gone after an Ubuntu's automatic update that I just applied.

---

### Post by cpsj on 2016-09-21
Thanks Jose, I have applied the recent update and Nautilus behaves a lot better. However the open windows are not shown on the launch window icon (as tick marks) making them hard to find on a busy screen.

---

### Post by shag00 on 2016-09-22
Still a problem.

---

### Post by mc4man on 2016-09-24
> **shag00 said:**
> Still a problem.

You could try this - 
Make sure there is a folder   on the Desktop, if not create one.
Right click on the nautilus icon in unity launcher > Unlock from Launcher
Open a terminal > run
```
nautilus -q
```
Now d. click on folder, on the launcher icon that appears  > Lock to Launcher
see if that improves.

---


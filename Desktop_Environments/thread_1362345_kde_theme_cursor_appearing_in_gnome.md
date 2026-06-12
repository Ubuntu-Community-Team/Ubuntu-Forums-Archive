---
title: "kde theme cursor appearing in gnome"
date: 2009-12-23
forum: Desktop Environments
---

### Post by ganeshguru on 2009-12-23
i have uninstalled my kubuntu-desktop from my ubunutu 9.10, but still kde cursor(Air theme) is appearing when i login using gdm.
i want my gnome cursor back.

---

### Post by Ekeluo on 2009-12-23
You can choose your cursor theme in the appearance properties dialog.

---

### Post by ganeshguru on 2009-12-23
i did that, but kde cursor is set as default cursor. i want to change the default cursor.

---

### Post by Zorael on 2009-12-23
```
$ sudo update-alternatives --config x-cursor-theme
```
The KDE default is **oxy-white**, and I guess the GNOME one is human-something-or-another. Enter its number and the system-wide default should get changed.

---

### Post by khmonir on 2009-12-28
> **Zorael said:**
> ```
$ sudo update-alternatives --config x-cursor-theme
```The KDE default is **oxy-white**, and I guess the GNOME one is human-something-or-another. Enter its number and the system-wide default should get changed.
[B]
I have the same problem but I have both Ubuntu and Kubuntu in my computer

I did what you said but I  still have the KDE cursor in firfox window and the GNOME cursor in Ubuntu

How can I solve this problem?
[/B]

---


---
title: "Show Applications - Frequent"
date: 2019-03-11
forum: Desktop Environments
---

### Post by Geoff_Lane on 2019-03-11
Folks,

Running 18:04 and finding the new Gnome desktop not a lot difference in appearance to Unity.

Strangely, if I click on the applications icon (bottom left) it shows a list of frequently used applications - except a couple of applications I use frequently seldom show on this list.

Appreciate easy to find by thyping name in search box but just wondering why some frequently used apps don't show in the frequently used apps window.

Geffers

---

### Post by DuckHook on 2019-03-11
> **Geoff_Lane said:**
> …except a couple of applications I use frequently seldom show on this list.
Do you mean to say that they *never* show on the list? See below…
> Appreciate easy to find by thyping name in search box but just wondering why some frequently used apps don't show in the frequently used apps window…
To show up on the applications screen, the app needs a *.desktop* file in either of two locations:

[LIST=1]
[*]```
/usr/share/applications
```
[*]```
~/.local/share/applications
```
[/LIST]
Instructions for creating *.desktop* file: [https://linuxconfig.org/how-to-create-custom-desktop-files-for-launchers-on-linux](https://linuxconfig.org/how-to-create-custom-desktop-files-for-launchers-on-linux)

---

